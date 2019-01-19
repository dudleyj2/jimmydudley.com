# [www.jimmydudley.com](https://www.jimmydudley.com)

To create my personal website, I pulled from a variety of sources.  Since I know there are others like myself that are constantly digging through source code, I figured I would save some time by organizing it for you.

## Design and Layout

My website was created using a few different libraries.  I imported the [jQuery](https://jquery.com/) javascript library into [main.js](https://github.com/dudleyj2/jimmydudley.com/blob/master/jimmydudley.com_V2/js/main.js).  Additionally, I used the [Font Awesome](http://fontawesome.io) library in my [main.css](https://github.com/dudleyj2/jimmydudley.com/blob/master/jimmydudley.com_V2/css/main.css) file for help in creating my design.

## Web Hosting

My site is hosted in an S3 bucket through Amazon Web Services.  They provide great documentation for all of their tools, including a convenient [guide](https://docs.aws.amazon.com/AmazonS3/latest/dev/website-hosting-custom-domain-walkthrough.html#root-domain-walkthrough-before-you-begin) for setting up your own static website.

I recommend registering your domain name through Route 53 on AWS.  I went the extra mile and was able to easily set up an SSL certificate using the AWS Certificate Manager and create a CDN for redirecting HTTP to HTTPS using AWS CloudFront.  I found [this](https://www.josephecombs.com/2018/03/05/how-to-make-an-AWS-S3-static-website-with-ssl) guide to be very helpful in setting all this up.

## Built With

* HTML
* CSS
* JavaScript
* AWS

## Author

* **Jimmy Dudley** - *dudleyj2@miamioh.edu*