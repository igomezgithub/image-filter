# Image Filter Starter Code

It allows users to register, log into, upload photos and filter an image from public URL.

The project repository can be downloaded from Github:
1. [The Image Filtering Microservice](https://github.com/igomezgithub/image-filter.git) It is a Node-Express application which runs a simple script to filter the public images.

## Tasks

### Setup Node Environment

You'll need to create a new node server. Open a new terminal within the project directory and run:

1. Initialize a new project: `npm i`
2. run the development server with `npm run dev`

### Testing in Dev environment

I have included a Postman config file with the RestAPI endpoints to launch several integrated tests.

The steps to start the **Image Filter Starter Code** feature test are as follows:

1. Open the Postman app and import this file **integrated-testing-restapi.postman_collection.json** (you can see it in the root of the project).
2. You must registry any user. Select this POST: *integrated-testing-restapi/Public/api/v0/user/auth valid registration*. Go to the **Body** section and write this json with your email and password. For example:
 
```json
{
	"email":"test@mail.com",
	"password":"test123"
}
```
3. In the **Headers** section you can add this row:

```
{
	KEY = Content-Type,
	VALUE = application/json
}
```

4. Click on **Send** button and the response should be '201 Created'. 
5. Copy the **token** string (from json response) 

    Note: you can skip these 5 steps if you use the token shown at the bottom of this document.

6. Select this GET: *integrated-testing-restapi/Authorized/api/v0/feed/filteredimage authorized*.
7. Go to the **Authorization** section and select *Type = Bearer Token*. Finally, paste the token that you received in the previous request.
8. In the **Params** section you must add a new row with the public URL:
```
{
	KEY = image_url,
	VALUE = your_image_to_apply_the_filter
}
```
9. Below I show a list with several public links that can be used for testing:

- https://upload.wikimedia.org/wikipedia/en/a/a9/Example.jpg
- https://www.cleverfiles.com/howto/wp-content/uploads/2018/03/minion.jpg
- http://www.personal.psu.edu/jyc5774/jpg.jpg

10. Finally you can see the response *200 OK* and the image from URL will be displayed in the Postman response (with greyscale).

### Testing in AWS environment

You must use the same file **integrated-testing-restapi.postman_collection.json** from Postman to start the tests.

1. Open the collection menu on **'...'** button and select the *Edit* option.
2. In the *Variables* section you can change the CURRENT VALUE by this AWS URL **override-with-instance-elastic-beanstalk** where the application has been deployed. 

    Note: click on *Persist All* to apply all changes.

3. Implement the same test plan as in the previous section **Testing in Dev environment**

### Deploying your system

Follow the process described in the course to `eb init` a new application and `eb create` a new environment to deploy your image-filter service! Don't forget you can use `eb deploy` to push changes.

## Stand Out (Optional)

### Refactor the course RESTapi

All request of the course is working successfully.

### Custom Domain Name

NOT IMPLEMENTED
