# Software Engineering Challenge (Backend)

## Introduction

At OptimizeApp we spend all day figuring out how to get customers ads online as quickly and easily as possible. As a software engineer, you have to build software to streamline our advertising placement functions. Your task here is to decide whether uploaded media is suitable for an advertisement.

## Requirements

1. We value a **clean**, **simple**, working solution.
2. The application must be run in Docker, candidate must provide `docker-composer.yml` and `start.sh` bash script at the root of the project, which should setup all relevant services/applications.
3. We prefer PHP (Laravel/Lumen), but the solution can also be written in Symfony.
4. Candidates must submit the project as a git repository (github.com, bitbucket.com, gitlab.com). The repository must avoid containing the words `optimizeapp` and `challenge`.
6. The solution must be [production] ready.

## Problem Statement

1. Must be a RESTful HTTP API listening to port `8080` (or you can use another port instead and describe in the README)

2. Our providers have a number of restrictions for uploaded media that must be checked on upload.

    | Provider | Image Type | Restrictions                                     | Notes                                                      |
    | -------- | ---------- | ------------------------------------------------ | ---------------------------------------------------------- |
    | Google   | .jpg       | Must be in aspect ratio 4:3 <br />< 2 mb size    |                                                            |
    |          | .mp4       | < 1 minutes long                                 |                                                            |
    |          | .mp3       | < 30 seconds long<br />< 5mb size                |                                                            |
    | Snapchat | .jpg, .gif | Must be in aspect ratio 16:9 <br />< 5mb in size |                                                            |
    |          | .mp4, .mov | < 50mb in size<br />< 5 minutes long             | Must extract a preview image from the middle of the video. |

    When media is uploaded it must be checked, processed and stored. Accurate error messages must be sent when an upload fails.

3. The API must implement 3 endpoints as described below
    - One endpoint to list providers. Providers are listed above and their rules should be provided as a description.
    - One endpoint to upload images
        - To create a image you must supply `name`, `provider`, `image_file`
        - The API responds with an object of the image
        - The provider should be an id from the provider table.

    -	One endpoint to upload videos
    	-	To create a video you must supply `name`, `provider`, `video_file`
    -	The API responds with an object of the video
    	-	The provider should be an id from the provider table.

    - One endpoint to list uploaded files
      - This should list all uploaded files showing the most recent first. This endpoint should be paginated.

4. The request input should be validated before processing. The server should return proper error responses in case validation fails.

5. A database must be used (at OptimizeApp we typically use MySQL). Database installation and initialization must be done in `start.sh`

6. All responses must be in json format for success and failure responses.

7. Relations between models can be made however they make sense. If extra tables are needed please make them.

8. Tables should have migrations

## Bonus Tasks
1. Having unit/integration tests is a strong bonus.
2. Add seeders
3. Add filters for media type, upload date


Questions? We love to answer: admin@optimizeapp.com
