---
layout: post
title: Writing unit tests for the Django models and why is it important?
date: 2017-07-05T19:41:00.000Z
published: true
tags:
  - testing
  - django
  - python
categories:
  - GSoC-2017
  - testing
  - django
  - python
---

You must have heard about the term test-driven-development if you are into the developmental works. It is the development in which you write tests before writing the logic. That means first you write the stuff that can break the code and then you write the real code that doesn't break which is unbreakable from that point of view.

I hope this makes sense. If not, keep on reading for some time and you will come to know more about the stuff.

## Why do we need tests?

At the intermediate level of development, where I am right now, we merely write tests for our code. But it is regularly said that

> Untested code is broken code.

That being said, I found a great presentation that will eventually strengthen my argument of writing automated tests.

[https://www.slideshare.net/wooda/philipp-von-weitershausen-untested-code-is-broken-code](https://www.slideshare.net/wooda/philipp-von-weitershausen-untested-code-is-broken-code)

First 7-8 slides will be enough to get the point across.

So the basic idea of automatic testing is to save someone from breaking our code in future and making the check as quickly as possible. This also helps us to find some issues in the code that were not visible when we coded them. The logical errors in the repository having thousands of lines of code are hard to detect. That is why the `good people` introduced testing for the developers.

Similarly in future, if someone codes something for us and we add that to our main repository without testing, it can break everything for us. So automatic testing is there to save us. Run the tests before adding the new stuff into the main repository and go forward without worrying about your code.

## What happens during testing?

During testing, we are given certain cases which are applied on the code. The output of the code is calculated and is compared with some recommended output that developer wants. If both the outputs are same then test passes otherwise it fails. As simple as that.

In the GSoC project, we wrote tests using the unittest module of python. The unit test is a software engineering term which means to test each and every module separately. This is the default testing module used by Django.

For the beginning, we used the module to write tests for the models in the code. Here is the commit for the code.

[https://github.com/singh1114/scancode-server/commit/99a36d8fe0c9289a5fac608f02cbf34171abdf28](https://github.com/singh1114/scancode-server/commit/99a36d8fe0c9289a5fac608f02cbf34171abdf28)

After applying the tests I found a few errors in the code that I removed in the same commit.

## What should we test in models?

While testing models we should test all the custom methods in the models. We should also test that we cannot add stuff when the field is not given. Django takes care of most of the rest stuff.

As all the things are provided in Django by default so there is very less need of test most of the things in the recent versions. But you should test __str__ and plural name of the models visible in the admin panel.

As your tests start taking shape you will feel more confident about your code.

Let's have a coding sample:

```python    
from django.test import TestCase
class ScanInfoTestCase(TestCase):
    def test_scan_info_added(self):
        scan_info = ScanInfo.objects.create(scan_type='URL', is_complete=True)
        self.assertTrue(scan_info.is_complete)
        self.assertEqual(scan_info.scan_type, str(url_scan_info))
        self.assertEqual('Scan Info', scan_info._meta.verbose_name_plural)
```


In the first line, we import the `TestCase` from django.test. After that, in the `ScanInfoTestCase` we inherited this `TestCase` and used `assertTrue` and `assertEqual` method to check if the tests pass or not. The `assertTrue` method is used to check if the value is True or not. Similarly, assertEqual checks if the two variables are equal or not.

For running tests in Django, apply:
    
`$ python manage.py test`

## Conclusion

It is not difficult to write automatic tests for your code. You just have to be patient with tests. It takes some time to write tests and many times it feels useless. But in longer runs, it will benefit you and save a lot of your time.
