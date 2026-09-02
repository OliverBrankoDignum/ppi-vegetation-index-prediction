# ppi-vegetation-index-prediction
I did a student internship in Summer of 2025. The idea was to try and predict PPI vegetation index while given a satellite image of an area and PPI measurements within certain points on that same image, which would be saved in a CSV file. The output I created was a Jupyter notebook written in Python, and several images which machine learning models had created. I wanted to make my work presentable to all whom it may concern, but the original data and my notebook which I had written had a few properties which made it unsuited for for this, namely:

 1. Entire notebook is written in Croatian, making it inaccesible for people who don't speak it.
 2. On top of that, it is commented in informal language without proper usage of markdown cells. This wasn't a problem during the internship but is not something I      would want to be public ("Hey, can you explain this part for me?" type of comments).
 3. I wasn't certain the data I used, both the image and the CSV file, was publically available. I also couldn't find the link to original github repository                where internship text and data were located. This means that I couldn't be certain if publishing any of those was acceptable.
    
Points one and two I would fix simply by writing the polished notebook, but point three is contentious. To circumvent this problem I had decided to rewrite my whole internship anew using data which was the same in spirit, but for which I could guarantee was publicaly available. I used help of ChatGPT for this and came up with the following:

  1.The original satellite image I had worked will be replaced by a satellite image of a field in northeastern Bulgaria. It comes from public Sentinel-2 Level-2A
    Cloud-Optimized GeoTIFF collection hosted on AWS: https://registry.opendata.aws/sentinel-2-l2a-cogs/. I will leave the link to the original image here for 
    sake of completeness but it is 278 MB of data so I don't recommend downloading it: 
    https://sentinel-cogs.s3.us-west-2.amazonaws.com/sentinel-s2-l2a-cogs/35/T/NJ/2019/8/S2B_35TNJ_20190826_0_L2A/TCI.tif
    This image was cropped to a more manageable size and we will study its properties more deeply in the notebook once we get to it. Finall image we will be 
    working with is 'Sentinel2_Bulgaria_2019-08-26_RGB_StudyArea.tif'
   2.PPI was calculated from available observations. During my 2025. internship we didn't dwelve in depth on how PPI is calculated so I will keep this part 
   simple, and will explain the methodology in separate file.

My original internship task started with both of these files being given so I've had no problem asking ChatGPT for help here.

