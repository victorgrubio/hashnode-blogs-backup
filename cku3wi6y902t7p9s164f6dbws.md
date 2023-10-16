---
title: "How to create a Postman Collection from OpenAPI Docs"
seoTitle: "How to Create a Postman Collection from OpenAPI Docs"
seoDescription: "Easily create API request collections in Postman using OpenAPI."
datePublished: Tue Sep 28 2021 09:39:00 GMT+0000 (Coordinated Universal Time)
cuid: cku3wi6y902t7p9s164f6dbws
slug: how-to-create-a-postman-collection-from-openapi-docs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697362183477/d98283fa-2659-4bc5-885e-5e3a6df1cd91.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1632822733716/3xPF9ugaz.png
tags: web-development, documentation, apis, rest-api, hashnodebootcamp

---

In the [previous article of this series](https://www.victorgarciar.com/api-documentation-with-openapi), we learned how to create the documentation for your API using OpenAPI.

If you didn't check it out, what are you waiting for !?!? 😁😁

Today we will see in this brief tutorial how to create a [Postman](https://www.postman.com) collection from this documentation.

---

# Download API docs

> We have different ways to download the YAML file containing the documentation. It depends on how we store it.

### Swagger Editor

Swagger Editor stores the status of your last edition. Yet, if you have to delete information from your browser, all your progress may be lost! 🆘🆘

Swagger Editor is an excellent tool for fast editing and linting your files. However, if the documentation is large and will take you days, then use editors like Notepad++, Gedit, or VSCode to write it.

To download the API documentation file from Swagger Editor, we have to click on: `Edit`\-&gt; `Save as YAML`

![Save-as-yaml-swagger-editor.png](https://i.imgur.com/UtPeRW1.png align="left")

The browser will download an `openapi.yaml` file.

### SwaggerHub

Swagger Hub stores the information on its servers. There is nothing to worry about here 🤗 To download it, we have to click on our API project.

Once we are editing our project, we have to click on `Export` -&gt; `Download API` -&gt; `YAML Resolved`.

![Swaggerhub-export-process.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632820916125/6O3lg2uvh.png align="left")

I think this is the best format to do so. JSON will be valid as well, although I find YAML easier to edit.

---

# Import it to Postman

Now, go on and open Postman. If you don't have it, you can download it from [this link](https://www.postman.com/downloads/).

We are going to select the `APIs` tab.

![Postman-api-section.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632820815169/esC3Wjjrw.png align="left")

Then let's click on `Import` and select the OpenAPI docs file. Confirm that you want the Collection to act as `Documentation`

![Collection-generation-step.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632819244523/29-Ygx4ln.png align="left")

If you check the APIs section, the definition of your OpenAPI Documentation should appear.

![API-definition-postman.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632819312132/Iq4FyFRGE.png align="left")

Moreover, the generated collection will appear in the `Collections` tab. You should see something like this:

![Postman-collection.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632819332607/F9MHoaXf-.png align="left")

# Create a Mock Server in Swaggerhub

> Do you have a server to make requests to? NO? LET'S MOCK IT THEN!

Before testing our API, we have to create a *Mock Server* to make requests to! To do so, we are going to take advantage of the *Integrations* available at SwaggerHub.

Click on your API name inside the editor and delete `Integrations` tab.

![Integrations.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632820629074/PVe6HwLJV.png align="left")

Then, add new integration and select `API Auto Mocking`

![AutoMocking-selection.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632820597708/s6Sp1neBX.png align="left")

Set your API name to whatever you want. In this case, I defined `Idea API`.

![Form-with-api-name.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632820648785/ddgWp2h-N.png align="left")

Now the integration is completed. We have our mock server up and running! The address has the following format:

`https://virtserver.swaggerhub.com/<owner>/<api-name>/<version>`

In my case, this results in `https://virtserver.swaggerhub.com/victorgarciar/idea-api/1.0.0`

---

# Test!

> You can't say "It works!" if you haven't tested it yourself

Let's go back to our Postman Collection and set the "baseUrl" variable to the URL of our mock server.

Click on the Collection's name and select the `Variables` tab. You will have a variable there named "baseUrl" as mentioned. Delete the current value and paste your mock server URL!

![Postman-variables.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632820689933/ZNKmeNrYp.png align="left")

Now we have everything set up! Go to one of the requests and send it. You should see something like this:

![Postman-request.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632820727833/Hx28X-NLL.png align="left")

Of course, the results will make no sense since we are using a mock server. Don't forget!

---

# Summary

In this article, I hope you have learned:

* Downloading your API docs
    
* Importing it to Postman
    
* Creating a mock server in SwaggerHub
    
* Test your API with a mock server
    

I am HONOURED if you have reached this point. Thanks a lot for reading 💙

Hopefully, I was able to explain how to import OpenAPI docs to Postman and create a Mock Server in SwaggerHub to test it!

Reach out on [Twitter](https://twitter.com/VictorGarciaDev) to find more valuable content or just chat!

🐦 [@victorgarciadev](ttps://twitter.com/VictorGarciaDev)

😼 [https://github.com/victorgrubio](https://github.com/victorgrubio)

## References

* [Previous Article of the Series](https://www.victorgarciar.com/api-documentation-with-openapi)
    
* [OpenAPI Documentation](https://swagger.io/docs/specification/about/)
    
* [SwaggerHub Integrations](https://support.smartbear.com/swaggerhub/docs/integrations/api-auto-mocking.html)