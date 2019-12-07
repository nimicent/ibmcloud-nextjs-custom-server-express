

# Next.js w/ Custom Express Server example for IBM Cloud

* First you need  an account on [IBM Cloud](https://cloud.ibm.com/)


* Install [IBM Cloud CLI](https://github.com/IBM-Cloud/ibm-cloud-cli-release) and restart terminal, type `ibmcloud` to check

* To minimize number of specifications per deploy you can use an application manifest to deploy to IBM Cloud using [manifest.yml](https://i.imgur.com/OrllgDr.png). Change the name and host to what you want them to be.


<p align="center">
  <img src="https://i.imgur.com/VvgICrj.png">
</p>

Go into root directory, make sure you have permissions for everything.


<p align="center">
  <img src="https://i.imgur.com/VfokmYM.png">
</p>

``` bash
npm i --save
ibmcloud login --sso
ibmcloud target --cf 
ibmcloud app push
```
Watch deployment logs.

You should see ... 

<p align="center">
  <img src="https://i.imgur.com/LUCWCwO.png">
  
</p>

And that is it. You have Next.js example app on IBM Cloud. 🦑

If you are doing more than this example demo and it fails
  `ibmcloud cf logs [YOUR_APPSNAME] --recent` 
And watch it. I have been able to troubleshoot from them every time.

NOTE
I altered the `production` to `dev` in the start script of package.json bc I hadn't installed dotenv and was pursuing deployment of live instance solely.

## The idea behind the example

*A version of [Next's example/custom-server-express](https://github.com/zeit/next.js/tree/master/examples/custom-server-express) revised to [deploy to IBM Cloud](https://github.com/nimicent/ibmcloud-nextjs-custom-server-express).*

## The idea behind the example

Most of the times the default Next server will be enough but sometimes you want to run your own server to customize routes or other kind of the app behavior. Next provides a [Custom server and routing](https://github.com/zeit/next.js#custom-server-and-routing) so you can customize as much as you want.

Because the Next.js server is just a node.js module you can combine it with any other part of the node.js ecosystem. in this case we are using express to build a custom router on top of Next.

The example shows a server that serves the component living in `pages/a.js` when the route `/b` is requested and `pages/b.js` when the route `/a` is accessed. This is obviously a non-standard routing strategy. You can see how this custom routing is being made inside `server.js`.
