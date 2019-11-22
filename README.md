# IST590-Unit7
# Project 7 - WordPress Pentesting

Time spent: 5 hours spent in total

> Objective: Find, analyze, recreate, and document **three to five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Vulnerability Name or ID: Unauthenticated Persistent Stored XSS
  - [x] Summary: Post a comment with > 64k data in it and anytime you move your mouse you get a pop-up notification on the site if the comment is being displayed.
    - Vulnerability types: Unauthenticated XSS
    - Tested in version: 4.2
    - Fixed in version:  4.2.1
  - [x] GIF Walkthrough: ![GIF1](https://user-images.githubusercontent.com/22669092/69396033-d61b5f80-0c95-11ea-8fd0-1feff99bdeba.gif)
  - [x] Steps to recreate: Submit a comment with the entry:
        > <a title='x onmouseover=alert(unescape(/hello20%world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px <whatever you want, just over 64k of data, e.g. spam "A" a lot'></a>
  - [x] Affected source code: None
    - [Link](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-3440)
1. (Required) Vulnerability Name or ID: Authenticated Stored XSS
  - [x] Summary: Trigger XSS through a post, mousing over it will do it
    - Vulnerability types: Authenticated stored XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [x] GIF Walkthrough: ![GIF2](https://user-images.githubusercontent.com/22669092/69396766-488d3f00-0c98-11ea-8828-04ab21333d86.gif)
  - [x] Steps to recreate: Create a new post with the body: 
        > <a href="[caption code=">]</a><a title=" onmouseover=alert('test') ">link</a>
  - [x] Affected source code:
    - [Link 1](https://klikki.fi/adv/wordpress3.html)
1. (Required) Vulnerability Name or ID
  - [x] Summary: Use a youtube url embed but woah it's actually XSS oops
    - Vulnerability types: Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
    - Tested in version: 4.2
    - Fixed in version: 4.2.13
  - [x] GIF Walkthrough: ![GIF3](https://user-images.githubusercontent.com/22669092/69396469-2941e200-0c97-11ea-9d03-680a29ee61fb.gif)
  - [x] Steps to recreate: Make a post and use code: 
        > [embed src='https://youtube.com/embed/videoURL<svg onload=alert("put a message in here")>'][/embed]
  - [x] Affected source code:
    - [Link](https://core.trac.wordpress.org/changeset/40160/trunk/src/wp-includes/embed.php?old=38361&old_path=trunk%2Fsrc%2Fwp-includes%2Fembed.php) 

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Took me a while to figure out you couldn't 

## License

    Copyright [2019] [Navjot Gill]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
