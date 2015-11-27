+++
date = "2015-11-27T10:46:25-05:00"
title = "Website translation that doesn’t suck."

+++
<script type="text/javascript">
$(document).ready(function() {
  $('.cr-btn').click(function (e) {
    if(!$(this).hasClass('disabled')) {
      e.preventDefault();
      if(navigator.userAgent.toLowerCase().indexOf('chrome') > -1) {
        mixpanel.track("Start install");
        chrome.webstore.install("https://chrome.google.com/webstore/detail/jnhmkblbgggfgeebimebebnkhgnagnpj", function() {
          // success callback
          // $(".cr-btn").addClass("disabled").text('BabelFrog is already installed');

          var mixpanelTrack = new $.Deferred();
          var gaTrack = new $.Deferred();
          $.when(mixpanelTrack, gaTrack).done(function() {
            window.location.href = "/help?install=inline";
          });

          _gaq.push(['_trackEvent', 'Engagement', 'Install', 'Inline']);
          _gaq.push(function() {
            gaTrack.resolve();
          });

          mixpanel.track("Install successful", undefined, function() {
            mixpanelTrack.resolve();
          });
        });
      }
      else {
        alert("Sorry, your browser does not support installing the Chrome extension.");
      }
    }
  });
});
</script>

**BabelFrog** is a light-weight Chrome extension that helps you read foreign websites by translating the text you select, not the whole page.

<div class="babelfrog-demo"><img src="/img/babelfrog-demo-4.gif"/></div>

Start reading websites in the original language, instead of waiting for a butchered machine translation.

<div class="button-wrapper">
<a class="button cr-btn" href="https://chrome.google.com/webstore/detail/babelfrog/jnhmkblbgggfgeebimebebnkhgnagnpj">
Add BabelFrog to Chrome
</a>
</div>

Unlike similar extensions, BabelFrog isn't bloated with features. It won't slow down Chrome, or ask you for permission to steal data from every website you visit.
