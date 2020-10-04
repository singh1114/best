---
layout: post
title: Faster validation of request parameters using middleware in node.js
date: 2019-07-05T15:55:00.000Z
updated_date: 2020-05-30T13:44:57.012Z
description: Validate your request parameters using a validator middleware that
  can be plugged into any Nodejs/ Express application or using JOI or AJV.
published: true
image: https://i.imgur.com/4BWtPKb.png
tags:
  - nodejs
  - technology
  - javascript
  - productivity
categories:
  - nodejs
  - technology
  - javascript
  - productivity
---
{% include lazyload.html image_src="https://i.imgur.com/4BWtPKb.png" image_alt="Validate your request parameters using middleware in node.js" image_title="Validate your request parameters using a middleware" %}

JavaScript being a [weakly typed](https://stackoverflow.com/questions/964910/is-javascript-an-untyped-language) language makes it is really hard for developers to validate any type of variables.

Lack of consistency and a well-defined framework doesn't help either.

A few months ago while working on big Node.js application, handling millions of requests per hour, I noticed it too.

Every API was literally checking if a certain parameter was being passed by the frontend correctly.

The same validations were repeated all over the codebase again and again.

Every time I had to create a new route/new API endpoint I had to write the same validation code.

For a [OOP based programmer turned JS developer](https://ranvir.xyz/blog/intermediate-guide-for-node.js-developers/) this was a bit of a shock.

For example:

```javascript
// Inside the route. 
if (!request.phone_number) {
    throw new Error('Main request parameter not present.');
}
```

> In this post we are going to learn the simplest way in which you can validate your request parameter or any other thing for that matter.

If you are starting out your app, this might look okay to you but as your app keeps getting bigger and bigger, you might want to write some specific validation code that can handle this for you out of the box.

If you're just getting started for your application, I would suggest you skip this article( But do [subscribe](https://ranvir.xyz/blog/subscribe/) so that you can receive other good stuff that I write about) and come back to it when you have some good number of developers editing your code.

This article is for someone who wants to wrap all his requests with some special validations.

This will also be helpful for your backend developers to know which parameters are required for the given route and which of them are optional. All you need to do is create a **middleware** which will keep account of all your parameters.

A good example for which middleware can be used is logging. You can log your request parameters, headers, response data to whatever logging system you are using.

We are only going to talk about a specific type of middleware in this article, but you can extend it to anything you want to.

## A middleware that can validate the request parameters.

How would you feel when you don't have to worry about the incoming request parameters in the routes?

Pretty awesome, right!

You will never have to make any check related to the request parameters. All these checks will be transported to this single middleware.

## What is a middleware?

> Middleware is a piece of code that is used to make changes to request or response data.

Let's start by writing a simple request validation middleware.

<script src="https://gist.github.com/singh1114/766113f61c4f61b8357e4ff0223ec3c1.js"></script>

So this is the simple structure of middleware in Node.js. There are three types of checks that are going on in there.

## Required Parameter check

This check tries to find if the parameter being requested is required or not. We can specify this while specifying the schema of the route parameters. I will share this schema a little later in this tutorial. If the parameter is required for the route and is not present in the parameters of the route, it will simply raise 400.

This can also give a custom message specifying which param exactly is not present in the request parameters. This part is described `on line 21`.

## Type check

JavaScript being less strict related to the type of the variables, we want to add a check which will try to check if the type specified in the schema of the route parameters is the same as the type received from the request parameters.

This part of the code is written `on line 6`.

## Other validation checks

There are multiple occasions when you want to add your own validations to request parameters. For example, you don't want the value to be equal to 0. You can simply create the function and pass it in the schema of the route parameters. These checks are written `on line 13`.

Here is the schema for route parameters.

<script src="https://gist.github.com/singh1114/e33ef5764df3476bf7a6c83cf3e9359d.js"></script>

This is how you will create a route in your `NodeJS` app.

The cool thing about this is you can at any time integrate your own checks into this and you don't have to worry about the error messages passed to frontend. They are handled as well.

### Simple Validator Required Parameter check

Following error is produced when the required parameter is not present in the request body.

{% include lazyload.html image_src="https://i.ibb.co/R9KgJHK/simple-validator-required.png" image_alt="Simple Validator Parameter check" image_title="Joi Required Parameter check" %}

### Simple Validator Length check

The following error is produced when the length of the required parameter is not accurate.

{% include lazyload.html image_src="https://i.ibb.co/mt9tGtX/Simple-validation-length.png" image_alt="Simple Validator length check" image_title="Joi length check" %}

### Simple Validator Wrong type check

The following error is produced when the type of the required parameter is not accurate.

{% include lazyload.html image_src="https://i.ibb.co/WskRHZQ/Simple-validation-type.png" image_alt="Simple Validator Wrong type check" image_title="Joi Wrong type check" %}

## Checking the performance of Simple validator

The above validation is trying to apply three checks.

1. Given param, `abc` must be a present.
2. Given param, `abc` must be a String.
3. Given param, `abc` must be of length 10.

I will use all three of these scenarios and try to find out the time taken to raise the error and give back the response.

### How am I checking the performance?

Javascript provides a very clean way to find out the time taken from [one point to the next point](https://stackoverflow.com/a/18427652/5142559). All you have to do is write `console.time('')` at the place where you want to start and `console.timeEnd('')` where you want to stop.

Passed string will be used as a reference, for example, I am using `console.time('start')` and `console.timeEnd('start')`. i.e. the string passed should be the same, in both the cases.

I added them to the middleware code.

```javascript
const validateParams = function (requestParams) {
    return function (req, res, next) {
        console.time('start');
            ...
                if (!checkParamType(reqParam, param)) {
                    console.timeEnd('start');
                } else {
                    if (!runValidators(reqParam, param)) {
                        console.timeEnd('start');
                        ...
            } else if (param.required){
                console.timeEnd('start');
                ...
    }
};
```

Finally, I ran the APIs for each error type separately for 5 times and took their average. These were the final scores.

```javascript
No parameter present in the body: 0.3228ms
Wrong length of the parameter: 0.7242ms
Wrong type of the parameter: 1.131ms( Used integer)
```

## Writing tests for simple request parameter validation middleware

One of my colleagues asked me to write tests for this framework as this was going to be used at a lot of places and I agreed with him. But I was a little skeptical on how can we test this framework. After some Googling and StackOverflowing, I was able to test this framework. Here is the code for this.

<script src="https://gist.github.com/singh1114/61495aff847d0a527cb039aaf8ffa408.js"></script>

## Using Joi as an alternative to adding request parameter validator 

I later found that you can use [Joi](https://github.com/hapijs/joi) for adding validations to parameters. This is a good option and you can use it if you want.

They provide a lot of validations out of the box which are easy to plug in.

Of course, you will have to install Joi to use it.

```javascript
npm install joi
```

Your `50` line of middleware code will just reduce to `26` lines.

```javascript
const Joi = require('joi');
const lodash = require('lodash');

const validateParams = function (paramSchema) {
    return async (req, res, next) => {
        const schema = Joi.object().keys(paramSchema);
        const paramSchemaKeys = Object.keys(paramSchema);
        let requestParamObj = {};
        for (let key of paramSchemaKeys){
            requestParamObj[key] = lodash.get(req.body, key);
        }
        try{
            await Joi.validate(requestParamObj, schema);
        } catch (err) {
            return res.send(400, {
                status: 400,
                result: err.details[0].message
            });
        }
        next();
    }
};

module.exports = {
    validateParams: validateParams
};
```

The main thing to look at here is the 

```javascript
await Joi.validate(requestParamObj, schema);
```

Similarly, you will have to set up your `route` as follows.

```javascript
router.post('/abc', validateParams({
    abc: Joi.string().length(10).required(),
}), routeFunction);
```

Pretty clean right, I like this method more than creating something new of my own. But you will have to keep in mind that this will increase your bundle size. This is something that you have to think on your own and make a decision.

### Joi Required Parameter check

The following error is produced when the required parameter is not present in the request body.

{% include lazyload.html image_src="https://i.ibb.co/fvhb10d/Joi-Required.png" image_alt="Joi Required Parameter check" image_title="Joi Required Parameter check" %}

### Joi Length check

The following error is produced when the length of the required parameter is not accurate.

{% include lazyload.html image_src="https://i.ibb.co/SXZHM1L/Joi-wrong-length.png" image_alt="Joi length check" image_title="Joi length check" %}

### Joi Wrong type check

The following error is produced when the type of the required parameter is not accurate.

{% include lazyload.html image_src="https://i.ibb.co/NrTLym7/Joi-wrong-type.png" image_alt="Joi Wrong type check" image_title="Joi Wrong type check" %}

### Validator Success response

Successful response.

{% include lazyload.html image_src="https://i.ibb.co/QjvtJcc/Success.png" image_alt="Validator Success response" image_title="Validator Success response" %}

## Checking the performance of JOI validator

I am using the same setup as I was using while checking the performance of Simple validator. Following are the results.

```javascript
No parameter present in the body: 1.0778ms
Wrong length of the parameter: 5.6514ms
Wrong type of the parameter: 14.3162ms( Used integer)
```

I will use the same formula in the other libraries as well.

## Using ajv as an alternative to adding request parameter validator

Then, we tried `ajv` for validating our requests.

{% include lazyload.html image_src="https://i.imgur.com/MRuoSal.png" image_alt="Validate your request param using ajv in node.js" image_title="Validate your request parameters using a ajv" %}

### Why `ajv`?

`ajv` uses the `JSON` schema validation which is kind of a standard in any language, and we can keep using it, even if we move to another language in the future.

Also, they consider themselves as the fastest JSON schema validator out there and speed is something that we care for a lot.

Install ajv using the following command.

```javascript
npm install ajv
```
Finally, write the ajv validation middleware as follows.

```javascript
const Ajv = require('ajv');
const lodash = require('lodash');

const validateParams = function (paramSchema) {
    return async (req, res, next) => {
        const ajv = new Ajv({$data: true});
        const paramSchemaKeys = Object.keys(paramSchema.properties);
        let requestParamObj = {};
        for (let key of paramSchemaKeys){
            // Use req.query/req.params if you want to validate query params.
            requestParamObj[key] = lodash.get(req.body, key);
        }
        const validated = ajv.validate(paramSchema, requestParamObj);
        if (!validated) {
            return res.send(400, {
                status: 400,
                result: getCustomMessage(ajv.errors[0])
            })
        }
        next();
    }
};

const getCustomMessage = (errorObject) => {
    if (['minLength', 'maxLength'].includes(errorObject.keyword)) {
        return `${errorObject.dataPath.replace('.', '')} ${errorObject.message}`;
    }
    return errorObject.message;
};

module.exports = {
    validateParams: validateParams
};
```

All you have to worry about is the `ajv.validate` function, which is used to carry out the validations. Unlike Joi, this `validate` method is not [async](https://ranvir.xyz/blog/basic-introduction-to-node.js-async-await/).

The validation definition method is a little different for `ajv`.

```javascript
router.post('/abc', validateParams({
		properties: {
			abc: {
				type: 'string',
				maxLength: 10,
				minLength: 10
			},
		},
		required: ['abc']
	}), routeFunction);
```

### AJV Required Parameter check

Following error is produced when required parameter is not present in the request body.

{% include lazyload.html image_src="https://i.ibb.co/mcC3TDw/ajv-required.png" image_alt="AJV Required Parameter check" image_title="Joi Required Parameter check" %}

### AJV length check

Following error is produced when the length of the required parameter is not accurate.

{% include lazyload.html image_src="https://i.ibb.co/J5j2TZ5/ajv-wrong-length.png" image_alt="AJV length check" image_title="Joi length check" %}

### AJV Wrong type check

Following error is produced when the type of the required parameter is not accurate.

{% include lazyload.html image_src="https://i.ibb.co/f2YzG0P/ajv-wrong-type.png" image_alt="AJV Wrong type check" image_title="Joi Wrong type check" %}

## Checking the performance of AJV validator

I am using the same setup as I was using while checking the performance of Simple validator.

```javascript
No parameter present in the body: 97.44ms
Wrong length of the parameter: 62.88ms
Wrong type of the parameter: 82.227ms( Used integer)
```

According to the above numbers, it is pretty clear that middleware using a Simple validator does perform better by big margins. You can choose whichever you want to use.

## Edit 1: Using Express-Validation for the validation

[Express-Validation](https://www.npmjs.com/package/express-validation) is a package build on the top of Joi and can be used to validate your request parameters fairly easily. You don't have to worry about this writing a separate middleware.

Install the package using the following command.

```shell
npm i express-validation --save
```

Adding the middleware is as simple as the following code.

```javascript
const express = require('express')
const bodyParser = require('body-parser')
const { validate, ValidationError, Joi } = require('express-validation')
 
const loginValidation = {
  body: Joi.object({
    email: Joi.string()
      .email()
      .required(),
    password: Joi.string()
      .regex(/[a-zA-Z0-9]{3,30}/)
      .required(),
  }),
}
 
const app = express();
app.use(bodyParser.json())
 
app.post('/login', validate(loginValidation, {}, {}), (req, res) => {
  res.json(200)
})
 
app.use(function(err, req, res, next) {
  if (err instanceof ValidationError) {
    return res.status(err.statusCode).json(err)
  }
 
  return res.status(500).json(err)
})
 
app.listen(3000)
```


{% include lazyload.html image_src="https://i.ibb.co/Pm0kkv9/Screenshot-2020-05-30-at-8-20-53-PM.png" image_alt="Express-Validation middleware" image_title="Express-Validation middleware" %}

I hope you guys will like the idea behind the post. Please share it with your colleagues and let me know on social media platforms.

I am also open to other standards that are followed in the market. Please leave your ideas in the comments.