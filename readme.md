# Intro to GitHub Actions

**The Master Branch is arranged as a starter file - the repository with the completed workflow.yml file is stored in a
[separate repository](https://github.com/edxhayter/GitHub-Action-Python-Demo-Solution).**

This repository is what I use for my intro to GitHub Actions session. Included in the documentation section is a copy
of the slides I ran the session:

- Explaining the basics of GitHub Actions in the context of CI/CD 
- The components of a GitHub Action and outlining a few example use cases for a GitHub Action. 
- The rest of the repository is for the demo part of the session - the repository should be forked by the participants and the Action built together as a group.
- The final part of the session was a quiz testing retention.

## Project Contents

- Main.py 
  - this is our simple Python script that queries the corporate buzzword API and writes the response to a text file. 
- requirements.txt
  - this is a text file that outlines all the packages that are required for the project. This will be
  used in the action to install all the script dependencies and allow it to run on a runner.
- Slides used for the training session.

## Main.py

### Code:
  
```python
# Import requests package
import requests

# Send GET request to the API
url = "https://corporatebs-generator.sameerkumar.website/"
response = requests.get(url)

# Check if the request was successful
if response.status_code == 200:
    # Extract the generated phrase from the JSON response
    bs_phrase = response.json()["phrase"]

    # Save the phrase to a text file
    with open("corporate_bs.txt", "w") as file:
        file.write(bs_phrase)

    print("Corporate BS phrase saved to corporate_bs.txt")
else:
    print(f"Failed to retrieve data. Status code: {response.status_code}")

```

## Workflow.yml

The session requires participants and the session lead to build a GitHub action that on manual request runs the main.py script. The Action must also commit the changes to the repository so that the text file with the new phrase is kept after the Action is run.



