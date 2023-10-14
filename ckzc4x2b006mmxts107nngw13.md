---
title: "New Released - Webvium Dev"
datePublished: Mon Feb 07 2022 03:28:15 GMT+0000 (Coordinated Universal Time)
cuid: ckzc4x2b006mmxts107nngw13
slug: webviumdev
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1644203944861/MMYF7AkJRm.png
tags: android-app-development, programming-blogs, github, android-studio, github-actions-1

---

# Webvium Dev 

is now available to be downloaded at [https://mrepol742.github.io/webviumdev](https://mrepol742.github.io/webviumdev?ref=mrepol742.hashnode.dev).

In order to released the dev version without the needs of contacting us or making the source code public. I decided to took this too far. It took me 15 failed workflow and hours to make this thing possible, in the 16 attempt everything work seamlessly.

Here is my github action workflow code snippet:

~~~
      - name: Delete Meta Data
        run: rm -rf app/build/outputs/apk/dev/output-metadata.json;
      - name: Pushes to released Repository
        id: push_directory
        uses: cpina/github-action-push-to-another-repository@main
        env:
          API_TOKEN_GITHUB: ${{ secrets.API_TOKEN_GITHUB }}
        with:
          source-directory: app/build/outputs/apk/dev/
          destination-github-username: 'mrepol742'
          destination-repository-name: 'released'
          user-email: mrepol742@gmail.com
          commit-message: Initial Commit
          target-branch: dev
~~~

This run after building the apk. First it deletes the output-metadata-json so it won't be included once the directory got copied. Then the file inside the dev folder will be copied to the released repository.

This makes the distributions so fast since i just need to push the new changes and it'll automatically compiled the app and push it into the released repo in dev branch.

