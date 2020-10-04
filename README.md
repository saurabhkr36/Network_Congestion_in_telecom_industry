# Network_Congestion_in_telecom_industry

## Introduction
This is an interhall open IIT data analytics competition.
## Problem Statement
In the context of telecommunications industry, one of the most important issues that industry faces is network congestion. It has been shown that congestion, even if for smaller durations, has a negative impact on customer loyalty, especially in price sensitive markets. To solve this problem effectively, it becomes imperative for firms to be able to predict congestion in advance and take proactive actions. 
## Data
The data is collected in a span of 5 minutes for user level activity and tower level activity.
Data dictionary:
1.	cell_name : Cell tower number/name – Masked name for cell towers
2.	4G_rat: Tower supports 3G/4G indicator
3.	Par_year – Year under consideration (2018)
4.	par_month – Month under consideration (December)
5.	par_day – Day under consideration
6.	par_hour – Hour under consideration
7.	par_min – Minute bucket under consideration
a.	Buckets of 5 min interval. Eg: value of 15 implies statistics are compiled/aggregated over a time period from 10-15 mins
8.	subscriber_count: Count of total subscribers for the cell in the specified time period
9.	Usage data: Data usage by activity type; includes both upload and download bytes
  a.	web_browsing_total_bytes
  b.	video_total_bytes
  c.	social_ntwrking_bytes
  d.	cloud_computing_total_bytes
  e.	web_security_total_bytes
  f.	gaming_total_bytes
  g.	health_total_bytes
  h.	communication_total_bytes
  i.	file_sharing_total_bytes
  j.	remote_access_total_bytes
  k.	photo_sharing_total_bytes
  l.	software_dwnld_total_bytes
  m.	marketplace_total_bytes
  n.	storage_services_total_bytes
  o.	audio_total_bytes
  p.	location_services_total_bytes
  q.	presence_total_bytes
  r.	advertisement_total_bytes
  s.	system_total_bytes
  t.	voip_total_bytes
  u.	speedtest_total_bytes
  v.	email_total_bytes
  w.	weather_total_bytes
  x.	media_total_bytes
  y.	mms_total_bytes
  z.	others_total_bytes
10.	beam_direction: Tower beam direction
11.	cell_range: Cell tower range
12.	tilt: Cell tower tilt 
13.	ran_vendor: Service Vendor
14.	Congestion_Type: Type of congestion observed (Target Variable)
The dataset has 80k training instances and 25k testing instances
## Objective
The objective is to train machine learning models that use cell tower statistics such as usage, customer count, etc, to predict the type of congestion that might occur.
## Approach
### Data preprocessing and feature engineering
The output categories(congestion types) and features having categorical nature are encoded. 
Used principal component analysis to remove undesired features in the dataset. The removed features are: 'cell_name','Congestion_Type','par_year' and 'par_month'. 
Applied logarithmic transformation to the features and treat the zero values to prevent feature exploding(value infinitely large).
After logarithmic transformation, I've applied scaling using standard scaler of sklearn

### Model
I've used Hard Voting ensemble technique on Gradient Boosting & SVC. The VotingClassifier is used from sklearn.ensemble where the hard voting is used for comparing two classification algorithms Gradient boosting and Support Vector Classification.
In hard voting, It uses predicted class labels for majority rule voting. 
The metric used for evaluation is Matthews correlation coefficient.
## End Notes
The feature extraction and treatment was the major challenge in this dataset.
The ensemble algorithm predicted congestion types with MCC score of 0.71. 

