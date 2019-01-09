# MULTI REPO !!!

Suppose you have a list of repos like this:

    $ helm repo list
    NAME                    URL
    stable                  https://kubernetes-charts.storage.googleapis.com
    devel                   http://127.0.0.1:8879/charts
    published-on-aws        s3://your-bucket

And a wide variety of charts across a large number of versions for each chart.

In order to do some local chart development tasks, with historical or published version
you typically had to had up `requires.yaml` and rig up a `file:///` debug patch.

But with `helm-multi-repo` you can now search across a list of repos for any chart

    helm repo add an-alias multi://local/published-on-aws/stable

And when `helm install` or `helm fetch` occurs, each repo configured in your alias repo will be searched.

In production set `an-alias` URL equal to a verified secure endpoint, but in development set `an-alias` to a `multi://` endpoint for easier iteration cycles!

# NOTE

requires `ruby`
