---
title: Google’s authentication-less on-the-fly image resizing service
author:
  - name: carlo
    url: 'https://github.com/carlo'
    avatar: 'https://avatars.githubusercontent.com/u/1501?v=3'
publisher:
  url: 'http://github.com'
  name: GitHub
  domain: gist.github.com
isBasedOnUrl: 'https://gist.github.com/5379498'
datePublished: '2016-03-21T20:45:25.251Z'
dateModified: '2016-03-21T15:39:44.816Z'
sourcePath: _posts/2016-03-21-googles-authentication-less-on-the-fly-image-resizing-servi.md
published: true
inFeed: true
hasPage: false
inNav: false
_type: Code
_context: 'http://schema.org'

---
# Google's authentication-less on-the-fly image resizing service
    
    I found it while poking around the Google+ HTML.  Jotting down some notes felt
    like a good idea, so here goes.  If you know more about this API, let me know,
    please!
    
    (Word of warning: I spent ~30 minutes on both my experimentation and this here
    write-up, so it might not be the most thought-provoking, brilliant thing you
    read today.)
    
    
    ## Base URL
    
    &grave;https://images1-focus-opensocial.googleusercontent.com/gadgets/proxy&grave;
    
    
    ## Parameters:
    
    * &grave;url&grave;: original image URL
    * &grave;container&grave;: must be "focus" (i dunno lol)
    * &grave;refresh&grave;: time (in seconds) to cache it on G's servers
    * &grave;resize_w&grave;: width in pixels
    * &grave;resize_h&grave;: height in pixels
    
    You can either specify both &grave;resize_*&grave; parameters or just one.
    
    
    ## Examples
    
    Let's resize [that big panorama picture I took in Istanbul last year][1].
    
    Make it square, 300x300px:
    
        https://images1-focus-opensocial.googleusercontent.com/gadgets/proxy?url=https%3A%2F%2Fdl.dropboxusercontent.com%2Fu%2F7298%2Fblog%2FBlick_von_der_S%25C3%25BCleymaniye-Moschee.jpg&container=focus&resize_w=300&resize_h=300
    
    Make it 750px wide and keep the aspect ration:
    
        https://images1-focus-opensocial.googleusercontent.com/gadgets/proxy?url=https%3A%2F%2Fdl.dropboxusercontent.com%2Fu%2F7298%2Fblog%2FBlick_von_der_S%25C3%25BCleymaniye-Moschee.jpg&container=focus&resize_w=750
    
    
    ## Quirks
    
    At least in Chrome, opening the URL in the browser will force a download of a text file (which is actually a JPG).  Putting the URL in an &grave;<img>&grave; tag is fine.  Or just use &grave;curl&grave;.
    
    
    
    [1]: https://dl.dropboxusercontent.com/u/7298/blog/Blick_von_der_S%C3%BCleymaniye-Moschee.jpg