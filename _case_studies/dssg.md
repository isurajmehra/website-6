---
title: Center for Data Science and Public Policy, Workforce Data Initiative
site: https://dsapp.uchicago.edu/ 
authors: Matt Bauman
logo: chicago.png
forum_topic: "https://discuss.okfn.org/t/new-frictionless-data-case-study-published-center-for-data-science-and-public-policy/5898"
short_description: "Supporting state and local workforce boards in managing and publishing data"

---

## What is the project?

The Workforce Data Initiative aims to modernize the US workforce through the use of data. One aspect of this initiative is to help state and local workforce boards collect, aggregate, and distribute statistics on the effectiveness of training providers and the programs they offer. The US Department of Labor mandates that every eligible training provider (ETP) work with state workforce 
boards to track the outcomes of their students in order to receive federal funding.  We are building a suite of open-source tools using open data specifications in order to help make this a reality; this collection of tools is called the Training Provider Outcomes Toolkit (TPOT). This specific tool, the etp-uploader, is a website that state workforce boards can eploy for training providers to upload their individual-level data.

## What are the challenges you face working with data?

There are many hundreds or thousands of training providers within the purview of each workforce development board. Each one must securely upload their participant data to their workforce board. This means that the workforce development boards must be equipped to receive and validate the data.

Training providers range from small trade apprenticeships to community colleges to multi-state organizations, with a wide range of data sophistication. The ways in which the workforce data board collects participant outcomes must be easy and accessible to all organizations. At the same time, it must be easy for the board itself to automatically process and validate the datasets.

## How do you use the specs?

We use the frictionless data standard for table schemas to define the required columns and data value constraints.  This is decoupled from the code, allowing each state to precisely define their requirements and easily create custom instances of the site.  We expose this flexibility through a [Heroku build script](https://id.heroku.com/login).

We have modified the [goodtables-web project](https://github.com/frictionlessdata/goodtables-web) to add support for uploading to an S3 repository.  We’ve further extended it to allow for uploading metadata about the uploaded file after it is validated.  This metadata is uploaded as a separate file.  In the future, we may use the data package standard to describe these two files as a single data package.

## What else would you like to see developed?

I’m excited to see the new developments around goodtables-py 1.0 and beyond.  It will be nice to eventually move our upload website to the new APIs. One  possible area for improvement in the goodtables-web validator is better error messages when specific data values do not match constraints.  I’ve imagined using adding a custom “data_constraint_error” field to the JSON table schema that would allow for friendlier errors, or perhaps dynamically generating such error messages using the constraints themselves.

## What do you think are some other potential use cases.

 I think that this general structure — a validated table upload tool — is very useful and could be used for a wide variety of applications.  It may make sense to allow for even more easy customizations to the site.

## Who else do you think we should speak to.

Abe Gong, author of Great Expectations

The  extension to goodtables-web is open source and available [here](https://github.com/workforce-data-initiative/etp-uploader) with a demo also running at [http://send.dataatwork.org](http://send.dataatwork.org)