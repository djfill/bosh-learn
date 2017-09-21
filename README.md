# BOSH-Learn

These instructions are a mixture of two tutorials - [Deploy BOSH on Google Cloud Platform](https://github.com/cloudfoundry-incubator/bosh-google-cpi-release/blob/master/docs/bosh/README.md) and [A Guide to Using BOSH](http://mariash.github.io/learn-bosh/#create_release).

## The reason for combining the two guides:
1. I wanted my BOSH instance in the Cloud rather than hosted locally on Virtualbox
2. I wanted to test my BOSH instance with a simple application rather than an expensive Cloud Foundry deployment
3. After following [Deploy BOSH on Google Cloud Platform](https://github.com/cloudfoundry-incubator/bosh-google-cpi-release/blob/master/docs/bosh/README.md), trying to deploy the smaller application described in [A Guide to Using BOSH](http://mariash.github.io/learn-bosh/#create_release) didn't work. This repository contains the BOSH v2 manifest that deploys successfully.

## Step by step guide

1. Follow the instructions as described [here](https://github.com/cloudfoundry-incubator/bosh-google-cpi-release/blob/master/docs/bosh/README.md) up to # Deploy other software
2. 
3. SSH on to the bosh bastion:
   gcloud compute ssh bosh-bastion
4. Clone this repository: 
   git clone https://github.com/djfill/bosh-learn.git
5. 

