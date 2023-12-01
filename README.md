## Continuous Deployment using AWS Code Pipeline and S3
Code for a game is hosted in GitHub.  We create an S3 bucket for static website hosting, then create a continuous deployment pipeline (using AWS Code Pipeline) to automatically deploy the code whenever changes are made.

![Screenshot](/images/CodePipeline.png)

### [🌐 LIVE SITE](http://my-meme-game-jm-3023.s3-website-us-east-1.amazonaws.com/)

## The Game
A simple memory matching game.  The user clicks two cards (images of memes) to try to match them.  If there's a match, the cards disappear from the board.  If there's no match, the cards are flipped back to their blank side so the user can try again.

The game consists of HTML, CSS and JavaScript.

Ideas for additional features:
- A scoring mechanism
- A timer
- Add additional cards
- Multi-player capabilities so you can compare scores 

## Bucket policy
Use this code for your bucket policy.  This allows everyone to read/view everything in the bucket.  Be sure to update the Bucket-Name.

  ```bash
        {
            "Version": "2012-10-17",
            "Statement": [
                {
                    "Sid": "PublicReadGetObject",
                    "Effect": "Allow",
                    "Principal": "*",
                    "Action": [
                        "s3:GetObject"
                    ],
                    "Resource": [
                        "arn:aws:s3:::Bucket-Name/*"
                    ]
                }
            ]
        }

   ```

## The Deployment Environment
The code will be deployed and hosted in S3.

## The Deployment Pipeline
The pipeline is created using AWS Code Pipeline.  The pipeline pulls the code from GitHub, and deploys it to S3 whenever a change is detected in the code.

## Cost
All services used are eligible for the [AWS Free Tier](https://aws.amazon.com/free/).  However, charges will incur at some point so it's recommended that you shut down resources after completing this tutorial.
