<h1>Varnish</h1>

A reverse proxy server that is used as a cache mechanism for Apache page requests. Varnish listens on port 80, but it can be bypassed by directly accessing Apache on port 8080.

The Varnish secret key for the box is 04788b22-e179-4579-aac7-f3541fb40391, you will need this when using the Varnish modules in Drupal.

Also you will need to select 3.x as your Varnish version and set the Varnish Control Terminal to be 127.0.0.1:6082.

This module can be found at [https://www.drupal.org/project/varnish/](https://www.drupal.org/project/varnish/).

<strong>NOTE</strong>: Varnish can get in the way of some functionality. If you are trying to run XDebug or XHprof then you might find that you need to access Apache directly or you won't see any responses coming through. Varnish can also cause some issues with anonymous users when certain cookies are required as the cookies tend to be blocked by Varnish.
