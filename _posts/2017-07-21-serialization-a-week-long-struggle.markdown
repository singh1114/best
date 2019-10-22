---
title: 'Serialization in Django: A week-long struggle'
date: 2017-07-21 22:53:00 Z
categories:
- GSoC-2017
- python
author: ranvirsingh1114
comments: true
link: https://ranvirsinghprojects.wordpress.com/2017/07/22/serialization-a-week-long-struggle/
wordpress_id: 812
layout: post
---

Hello folks,

I have been away from my blog because there was nothing really to discuss. I was constantly trying to do some stuff and was constantly failing. But, after a week long struggle and some help I was able to get over this struggling period and now shifted to the next task in my task list.

So as a whole, this month was well spent learning new stuff, first unit tests and then serializers. Those who have worked with Django Rest Framework will get what I am trying to say in the post.

First things first, **Why do we need serializers?**

To answer this question, we need to know what serialization is?

According to Wikipedia, serialization is the process by which we convert the data into such a format so that it can be transferred easily through the different layers of electronic components.

We know that our data is present in the models. We also know that we cannot ship that data easily to different formats through our models. So, we use the simple concept of serialization that converts the models' data **or any other data **into JSON, XML or YAML format which can be easily transmitted over the network.

Easy, right?

Let's dive in and see some code snippets.

[sourcecode language="python" wraplines="false" collapse="false"]
class ScanInfo(models.Model):
    def __str__(self):
        return self.scan_type

    scan_types = (
        ('URL', 'URL'),
        ('Local Scan', 'localscan'),
    )

    scan_type = models.CharField(max_length=20, choices=scan_types, default='URL')
    is_complete = models.BooleanField()

class UserInfo(models.Model):
    def __str__(self):
        return self.user.username

    user = models.OneToOneField(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    scan_info = models.ForeignKey(ScanInfo)

class URLScanInfo(models.Model):
    def __str__(self):
        return self.URL

    scan_info = models.ForeignKey(ScanInfo)
    URL = models.URLField(max_length=2000)

class LocalScanInfo(models.Model):
    def __str__(self):
        return self.folder_name

    scan_info = models.ForeignKey(ScanInfo)
    folder_name = models.CharField(max_length=200)

class CodeInfo(models.Model):
    def __str__(self):
        return self.total_code_files

    scan_info = models.ForeignKey(ScanInfo)
    total_code_files = models.IntegerField(null=True, blank=True)
    code_size = models.IntegerField(null=True, blank=True, default=0)

[/sourcecode]

Well, that's not the all of the models, but you got the idea, right? So, we have multiple levels of inheritance between all those models( Well not really inheritance but in simple words, we can say this). Now the real test is to write the serializers about them.

I decided to use the simple ModelSerializers.

[sourcecode language="python" wraplines="false" collapse="false"]
class ScanInfoSerializer(serializers.ModelSerializer):
    class Meta:
        model = ScanInfo
        fields = '__all__'
class UserInfoSerializer(serializers.ModelSerializer):
    class Meta:
        model = UserInfo
        fields = '__all__'
class URLScanInfoSerializer(serializers.ModelSerializer):
    class Meta:
        model = URLScanInfo
        fields = '__all__'
class LocalScanInfoSerializer(serializers.ModelSerializer):
    class Meta:
        model = LocalScanInfo
        fields = '__all__'
class CodeInfoSerializer(serializers.ModelSerializer):
    class Meta:
        model = CodeInfo
        fields = '__all__'
[/sourcecode]

Now I checked the sample outputs of these serializers and to my surprise, I was not able to get the desired result. The JSON output created by them was totally opposite from what we were expecting it to be.

So, I did an experiment to create a GodSerializer( Which was the literal name of the serializer) along with a helper for it. The helper will tell the serializer in the way that it was going to work.

[sourcecode language="python" wraplines="false" collapse="false"]
class GodSerializer(serializers.Serializer):
    """
    Another good serializer to handle all the serialization activities
    """
    code_info = CodeInfoSerializer()
    url_scan = UrlScanInfoSerializer()
    local_scan = LocalScanInfoSerializer()
    scan_result = ScanResultSerializer()
    scan_file_info = ScanFileInfoSerializer(many=True)
    license = LicenseSerializer(many=True)
    matched_rule = MatchedRuleSerializer(many=True)
    matched_rule_license = MatchedRuleLicenseSerializer(many=True)
    copyright = CopyrightSerializer(many=True)
    copyright_holder = CopyrightHolderSerializer(many=True)
    copyright_statement = CopyrightStatementSerializer(many=True)
    copyright_author = CopyrightAuthorSerializer(many=True)
    package = PackageSerializer(many=True)
    scan_error = ScanErrorSerializer(many=True)
[/sourcecode]

After this, I created the GodSerializerHelper that helped the Serializer the way things were going to work. Here is the code for the helper.

[sourcecode language="python" wraplines="false" collapse="false"]
class GodSerializerHelper(object):
    def __init__(self, scan_info):
        self.scan_info = scan_info
        self.code_info = CodeInfo.objects.get(scan_info=scan_info)
        self.url_scan = URLScanInfo.objects.get(scan_info=scan_info)
        self.local_scan = None
        self.scan_result = ScanResult.objects.get(code_info=self.code_info)
        self.scan_file_info = ScanFileInfo.objects.filter(scan_result=self.scan_result)
        self.license = License.objects.filter(scan_file_info__in=(self.scan_file_info))
        self.matched_rule = MatchedRule.objects.filter(license__in=(self.license))
        self.matched_rule_license = MatchedRuleLicenses.objects.filter(matched_rule__in=(self.matched_rule))
        self.copyright = Copyright.objects.filter(scan_file_info__in=(self.scan_file_info))
        self.copyright_holder = CopyrightHolders.objects.filter(copyright__in=(self.copyright))
        self.copyright_statement = CopyrightStatements.objects.filter(copyright__in=(self.copyright))
        self.copyright_author = CopyrightAuthor.objects.filter(copyright__in=(self.copyright))
        self.package = Package.objects.filter(scan_file_info__in=(self.scan_file_info))
        self.scan_error = ScanError.objects.filter(scan_file_info__in=(self.scan_file_info))
[/sourcecode]

See the proper usage __in, this is used to remove a big error of calling a model by using multiple rows of the ForeignKey. This might seem weird explanation. But that's it. Let me try it once more. We know when we use objects.filter it return more than one row. Now as the variable is storing more than one row, it cannot be passed to next objects.filter because it has more than one rows itself.

After this, for testing, I used the following code to see if the things are looking well.

[sourcecode language="python" wraplines="false" collapse="false"]
s = GodSerializerHelper(ScanInfo.objects.get(pk=51))
s = GodSerializer(s)
s.data
[/sourcecode]

Hope this post helps someone in future. Still, in some dilemma, join the conversation in the comments.

Have a good day.
