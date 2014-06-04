google-signin-samples
=====================

Some samples showing how to use the [`google-signin`](https://github.com/GoogleWebComponents/google-signin)
Polymer element in your own custom elements.

Basically what you have to do is to include a `google-signin-aware` element
in your custom elements, define the scopes you need, and wait for a
`google-signin-aware-success` event. You can then use the provided access token,
or the authenicated `gapi.client` to make calls to Google APIs.

To make this work you also need to include a `google-signin` element that actually
handles the Authentication somewhere on the page (outside of your element), and
define your Client ID (from the [Google Developers Console](https://console.developers.google.com/)).
While not strictly necessary I recommend also defining all scopes you will need on
your page in the `google-signin` element. Especially some of the older GData scopes
work better that way.

This single `google-signin` element will then inform all `google-signin-aware` elements
of Authentication success/failure, so you can have multiple custom elements (with possibly
different scopes) making use of the single Sign-in button.

`google-signin-status` just displays name and profile image for the authenticated user

`google-plus-friends` displays a list of Google+ friends for the authenticated user

`picasa-photo-uploads` directly uses the access token (and some JSONP/CORS trickery)
to fetch recently uploaded photos from the (antiquated) Picasa Web Albums Data API.

`custom-google-signin` shows a way of getting rid of the (still) ugly `google-signin`
buttons by including a hidden `google-signin` element in a custom element, and then
directly calling the `signIn` and `signOut` methods of this element via nicer custom buttons.

`demo1.html` is a sample page that includes all samples elements and a `google-signin` element.
[Live Version](https://scary-experiments.appspot.com/google-signin-samples/demo1.html)

`demo2.html` is almost the same sample page but includes a `custom-google-signin` that renders nicer buttons.
[Live Version](https://scary-experiments.appspot.com/google-signin-samples/demo2.html)


```
Copyright 2014 Gerwin Sturm, FoldedSoft e.U. / www.foldedsoft.at

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```