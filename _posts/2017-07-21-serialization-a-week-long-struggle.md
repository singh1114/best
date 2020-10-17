---
wordpress_id: 812
layout: post
author: Ranvir Singh
title: 'Serialization in Django: How to serialize models with Foreign keys'
date: 2017-07-21T22:53:00.000Z
author_name: Ranvir Singh
author_username: ranvir_xyz
canonical_url: https://ranvir.xyz/blog/how-does-django-validate-passwords/
description: >-
  Explaining the process of serialization in Django containing the models with
  Foreign keys and create JSON response for the APIs.
published: true
comments: true
tags:
  - GSoC-2017
  - python
  - django
link: >-
  https://ranvirsinghprojects.wordpress.com/2017/07/22/serialization-a-week-long-struggle/
categories:
  - GSoC-2017
  - python
  - django
---

Serialization is one of the main processes of creating APIs. We want to share data between different types of frontends (Web, Android, IOS) in a way that is easily accessible by them all. Serialization is the process of converting different data into a well-defined format and send it as the API response.

I have been away from my blog because there was nothing really to discuss. I was constantly trying to do some stuff and was constantly failing. But, after a week-long struggle and some help I was able to get over this struggling period and now shifted to the next task in my task list.

So as a whole, this month was well spent learning new stuff, first [unit tests](https://ranvir.xyz/blog/writing-unit-tests-for-the-models/) and then serializers.

## Prerequisites 1: Django

First things first, **Why do we need serializers?**

We know that our data is present in the database. We also know that we cannot send that data easily to different formats through our database. So, we use the simple concept of serialization that converts the database data **or any other data **into JSON, XML or YAML format which can be easily transmitted over the network.

Easy, right?

Let's dive in and see some code snippets.

Here is the model file of my **GSoC-2017** project.

```python
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
```

Well, that's not all the models, but you get the idea, right? So, we have multiple levels of inheritance between all those models (Well not really inheritance but in simple words, we can say that). Now the real test is to write the serializers for them so that we don't have to write a separate function to convert data to JSON.

I decided to use simple ModelSerializers.

```python
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
```

Now when I checked the sample outputs of these serializers and to my surprise, I was not able to get the desired result. The JSON output created by them was totally opposite from what we were expecting it to be. I was expected everything to available in a way as the models were defined.

I was expecting that the Foreign keys will be handled on its own like we would define the models in [NoSQL database](https://ranvir.xyz/blog/mongo-aggregates/).

So, I did an experiment to create a GodSerializer along with a helper for it. The helper helped the `serializer` and told it about the way in which it should go forward with the serializing.

```python
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
```

After this, I created the GodSerializerHelper that helped the Serializer the way things were going to work. Here is the code for the helper.

```python
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
```

See the proper usage of `__in`, this is used to remove a big error of calling a model by using multiple rows of the `ForeignKey`.

Let me try it once more. We know when we use objects and `filter` it, it returns more than one row. Now as the variable is storing more than one row, it cannot be passed to next `objects.filter` because it has more than one row itself.

After this, for testing, I used the following code to see if the things are looking well.

```python
s = GodSerializerHelper(ScanInfo.objects.get(pk=51))
s = GodSerializer(s)
s.data
```

This gave me the proper and as intended response.

Hope this post helps someone in the future. If still in dilemma, join the conversation in the comments.

Have a good day.
