---
layout: post
section-type: post
title: Keep Code Left
category: tech
tags: [ 'pattern' ]
---

### Keep Code Left: 50% of "else" statements are unnecessary

Disclaimer: This post is based on a MeetUp talk given by a Sr Engineer.

50% of "else" statements are unnecessary. Not only that, but they increase bugs and
decrease readability and maintainability. A code pattern to counter this is the
"guard pattern". Thinking in terms of guard patterns instead of if/else puts you
in a frame of mind where you are more likely to catch bugs. Also, once this pattern
is established in a codebase, the readability (and thus maintainability) of that
codebase increases.

This is an example of

```javascript
addToRooms: function(messages){
  $('#roomSelect').html('<option value="newRoom">New Room...</option><option value="lobby" selected>Lobby</option>');

  if (Array.isArray(messages)) {
    var processedRooms = {};
    messages.forEach(function (message){
      var roomname = message.roomname;

      if (roomname && !processedRooms[roomname]) {
        app.addRoom(roomname);
        processedRooms[roomname] = true;
      }
    });
  }
 
  $('#roomSelelect').val(app.room);
}
```

Run the ./scripts/newpost script with the file name of the post as an argument:

<pre style="text-align: left">
cd <your { Personal } repo>
./scripts/newpost hello-world
</pre>

A a new post template with name YYYY-MM-DD-hello-world.md will be created under ./\_posts, with the current date.

In the created post, just replace the Title, Category and tags and you can
start writing your post in markdown right bellow the end of the post header.

Every file with the format <i>YYYY-MM-DD-post-title.md</i> will be processed as a
post, with publication date <i>YYYY-MM-DD</i>.

The content starts with:

<pre style="text-align: left">
---
layout: post
section-type: post
title: Title
category: Category
tags: [ 'tag1', 'tag2' ]
---
</pre>

The *layout* and *section-type* are used by the theme.

### Post navigation

You can navigate between the posts by swiping left/right in the post pages!

### Hashtags

Note: *{ Personal }* generates a static page, just like all Jekyll themes.
As a result we have to create the tag pages before building and publishing the site.

In order to generate the tag pages, simply run the *generate-tags* script from the repo's root directory:

<pre style="text-align: left">
./scripts/generate-tags
</pre>

The script will parse all your posts, and generate the tag pages for the newly added tags.

If you are not using Github Pages, you can automate the execution of this script during build time.
