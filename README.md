# Project 7 - WordPress Pentesting

Time spent: 7 hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1.Authenticated Stored XSS in YouTube URL Embeded
  - [ ] Summary: You can use XSS to access areas that you are not authenticated for 
    - Vulnerability types: XSS/ Inject
    - Tested in version: 4.2
    - Fixed in version:  4.2.13
  - [ ] GIF Walkthrough: https://imgur.com/a/JNhlG
  - [ ] Steps to recreate: 
      Choose an youtube video 
      Put this on the url "[embed src=‘https://youtube.come/embed/12345\x3csvg onload=while(1){alert(document.cookie};\x3e’][/embed]" 
      Post
      You can get an error message to the source
  - [ ] Affected source code:
    https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8

2.  Authenticated XSS
  - [ ] Summary:  You can use file meta data to authenticate
    - Vulnerability types: XSS/ Injection
    - Tested in version: 4.1.1
    - Fixed in version: 4.2.13
  - [ ] GIF Walkthrough: https://imgur.com/a/duHTa
  - [ ] Steps to recreate: 
      Add at least 3 media files
      Make the file description "Let it go <noscript/><script>alert(document.cookie);</script>" 
      Add this new file to a new post
      View the error message
  - [ ] Affected source code:
    - https://core.trac.wordpress.org/browser/tags/version/src/source_file.php

3. Authenticated Stored XSS  via Image Filename
  - [ ] Summary: Use XSS to get authentication through file names
    - Vulnerability types: XSS
    - Tested in version: 4.2.2
    - Fixed in version: 4.2.10
  - [ ] GIF Walkthrough: https://imgur.com/a/IvYm3
  - [ ] Steps to recreate: 
      - Choose an image
      - Name it "<img src=a onerror=alert(document.cookie)>.jpg"
      - Upload to WP
      - View the attachement
      - You can now see the image source
  - [ ] Affected source code:
      - (https://github.com/WordPress/WordPress/commit/c9e60dab176635d4bfaaf431c0ea891e4726d6e0



## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

- Gifs created with imgur and nvidia record
## Notes

Installing vagrant was a huge hassel for me 

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
