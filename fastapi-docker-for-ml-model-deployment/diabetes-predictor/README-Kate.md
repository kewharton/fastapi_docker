
Overview:

The goal of this project was to successfully deploy a machine learning model with FastAPI and Docker.

As instructed, I followed the tutorial which linked this wonderful repo: https://github.com/balapriyac/data-science-tutorials.git

to run the app locally:
    $ uvicorn app.main:app --reload --port 8000

test with curl that works:
    curl -X POST "http://localhost:8000/predict" \
  -H "Content-Type: application/json" \
  -d '{
    "age": 0.05,
    "sex": 0.05,
    "bmi": 0.06,
    "bp": 0.02,
    "s1": -0.04,
    "s2": -0.04,
    "s3": -0.02,
    "s4": -0.01,
    "s5": 0.01,
    "s6": 0.02
  }'


response: {"predicted_progression_score":213.34,"interpretation":"Above average progression"}

test with curl that doesnt work and returns error because of a missing field:
curl -X POST "http://localhost:8000/predict" \
  -H "Content-Type: application/json" \
  -d '{
    "age": 0.05,
    "bmi": 0.06,
    "bp": 0.02,
    "s1": -0.04,
    "s2": -0.04,
    "s3": -0.02,
    "s4": -0.01,
    "s5": 0.01,
    "s6": 0.02
  }'

response: {"detail":[{"type":"missing","loc":["body","sex"],"msg":"Field required","input":{"age":0.05,"bmi":0.06,"bp":0.02,"s1":-0.04,"s2":-0.04,"s3":-0.02,"s4":-0.01,"s5":0.01,"s6":0.02}}]}