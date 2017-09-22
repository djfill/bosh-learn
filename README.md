# BOSH-Learn

These instructions are a mixture of two tutorials - [Deploy BOSH on Google Cloud Platform](https://github.com/cloudfoundry-incubator/bosh-google-cpi-release/blob/master/docs/bosh/README.md) and [A Guide to Using BOSH](http://mariash.github.io/learn-bosh/#create_release).

## The reason for combining the two guides:
1. I wanted my BOSH instance in the Cloud rather than hosted locally on Virtualbox
2. I wanted to test my BOSH instance with a simple application rather than an expensive Cloud Foundry deployment
3. After following [Deploy BOSH on Google Cloud Platform](https://github.com/cloudfoundry-incubator/bosh-google-cpi-release/blob/master/docs/bosh/README.md), trying to deploy the smaller application described in [A Guide to Using BOSH](http://mariash.github.io/learn-bosh/#create_release) didn't work. This repository contains the BOSH v2 manifest that deploys successfully.

## Step by step guide

1. Follow the instructions as described [here](https://github.com/cloudfoundry-incubator/bosh-google-cpi-release/blob/master/docs/bosh/README.md) up to the 'Deploy other software' section.
   Note: I had to make the following change in Step 2 and 3 of 'Deploy Supporting Infrastructure')
   ```
   hashicorp/terraform:light
   to
   hashicorp/terraform:0.9.9
   ```
2. SSH on to the bosh bastion:
   ```
   gcloud compute ssh bosh-bastion
   ```
3. Clone this repository: 
   ```
   git clone https://github.com/djfill/bosh-learn.git
   ```
4. Upload the Cloud Config:
   ```
   bosh2 -e micro-google update-cloud-config cloud-config.yml
   ```
   a. View the Cloud Config:
   ```
   bosh2 -e micro-google cc
   ```
5. Upload the Stemcell:
   ```
   bosh2 -e micro-google upload-stemcell https://s3.amazonaws.com/bosh-core-stemcells/google/bosh-stemcell-3445.11-google-kvm-centos-7-go_agent.tgz
   ```
   a. View the stemcells:
   ```
   bosh2 -e micro-google stemcells
   ```
6. Create a Release:
   ```
   cd bosh-learn
   bosh2 -e micro-google create-release
   ```
   a. View the Releases:
   ```
   bosh2 -e micro-google releases
   ```
7. Deploy:
   ```
   bosh2 -e micro-google -d learn-bosh deploy manifest.yml
   ```
   a. View the Deployments:
   ```
   bosh2 -e micro-google ds
   ```
8. View the instances:
   ```
   bosh2 -e micro-google -d learn-bosh instances
   ```

   

