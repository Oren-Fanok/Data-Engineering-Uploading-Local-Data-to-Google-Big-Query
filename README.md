# Data-Engineering-Uploading-Local-Data-to-Google-Big-Query

# Overview

This code file is designed to take a sample of local csv files and upload them to cloud based storage within Google Big Query.

**local data and authentication keys not included for anonymity reasons.


# Process

We begin this file by conducting to our Goggle Big Query Project, and authenticating our service account. Once we have authenticated access we will begin our upload process by making our data funnel idempotent. I will check my project for any existing tables that match my regex search pattern and delete any matches.

Now that I have a clean GBQ project, I'll read in my local csv files, convert them to a pandas dataframe, and store them in a list. Next I will clean each dataframe by converting datatypes, removing dollar signs, and handling nulls. Finally I created a Year Month list based on the unique ym values in each dataframe. This allows me to upload monthly tables to GBQ. The program then iterates over each ym combination in the Year Month list and uploads a monthly table to GBQ.

As a final step I queried the recently uploaded tables to count the number of records per month and plotted the results.
