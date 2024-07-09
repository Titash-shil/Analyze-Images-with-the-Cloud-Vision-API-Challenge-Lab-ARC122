# Analyze Images with the Cloud Vision API: Challenge Lab || [ARC122](https://www.cloudskillsboost.google/course_templates/633/labs/461567) ||

# # Like, comment, share & Don't forget to subscribe [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN) 👍😄🤝

### Run the following Commands in CloudShell
```
export API_KEY=
```
```
gcloud config set compute/region $REGION


gsutil acl ch -u AllUsers:R gs://$DEVSHELL_PROJECT_ID-bucket/manif-des-sans-papiers.jpg

sleep 20

cat > request.json <<EOF
{
  "requests": [
      {
        "image": {
          "source": {
              "gcsImageUri": "gs://$DEVSHELL_PROJECT_ID-bucket/manif-des-sans-papiers.jpg"
          }
        },
        "features": [
          {
            "type": "TEXT_DETECTION",
            "maxResults": 10
          }
        ]
      }
  ]
}
EOF


curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json  https://vision.googleapis.com/v1/images:annotate?key=${API_KEY}

curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json  https://vision.googleapis.com/v1/images:annotate?key=${API_KEY} -o text-response.json

gsutil cp text-response.json gs://$DEVSHELL_PROJECT_ID-bucket


cat > request.json <<EOF
{
  "requests": [
      {
        "image": {
          "source": {
              "gcsImageUri": "gs://$DEVSHELL_PROJECT_ID-bucket/manif-des-sans-papiers.jpg"
          }
        },
        "features": [
          {
            "type": "LANDMARK_DETECTION",
            "maxResults": 10
          }
        ]
      }
  ]
}
EOF


curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json  https://vision.googleapis.com/v1/images:annotate?key=${API_KEY} -o landmark-response.json

gsutil cp landmark-response.json gs://$DEVSHELL_PROJECT_ID-bucket
```

# Congratulations ..!!🎉  You completed the lab shortly..😃💯

# *Well done..!* 👏

# Thank you for visiting.... :) 🗯️

# [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN) 




