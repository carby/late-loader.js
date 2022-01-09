# late-loader.js
Load scripts easily after body onload

# USAGE
Refactor you script tags and add last-loader.js *last*, eiher as a separate script or as an inline script:

    <script data-src='https://cdnjs.cloudflare.com/ajax/libs/jquery/3.0.0-beta1/jquery.min.js'></script>
    <script src='/js/late-loader.js'></script>

The refactorization is pretty straight foreward. Rename the *src* attribute to the same dataset attribute, *data-src*. Late-loader.js will now load the scripts dynamically based on browser events.

Late-loader.js also includes simple dependency management. Say your own scripts depends on jquery you can have late-loader.js load that script after jquery has loaded:

    <script data-src='https://cdnjs.cloudflare.com/ajax/libs/jquery/3.0.0-beta1/jquery.min.js' data-id='jq_script'></script>
    <script data-src='/js/my-bundle.js' data-dependency='jq_script'></script>
    <script src='/js/late-loader.js'></script>

Here the *my-bundle.js* will be loaded after jquery it has a dataset dependancy attribute matching the dataset id attribute of the script it depends on.

You have to be aware of two things though:
1. Late-loader.js must appear last of all the scripts it's supposed to handle.
2. Any 'id' attribute a script tag with a 'data-id' will be overwritten. This should be a narrow case.

Having late-loader.js as an inline script should be the fastest way to do it, since it saves one round-trip to the server.

Have fun + best wishes!
