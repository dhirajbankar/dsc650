---
title: Assignment 1
subtitle: Computer performance, reliability, and scalability calculation
author: Dhiraj Bankar
---

## 1.2 

#### a. Data Sizes

| Data Item                                  | Size per Item | 
|--------------------------------------------|--------------:|
| 128 character message.                     | 128 Bytes       |
| 1024x768 PNG image                         | 1.5 MB          |
| 1024x768 RAW image                         | 2.25 MB          |
| HD (1080p) HEVC Video (15 minutes)         | 160.18 MB          |
| HD (1080p) Uncompressed Video (15 minutes) | 160,180 MB          |
| 4K UHD HEVC Video (15 minutes)             | 640 MB          |
| 4k UHD Uncompressed Video (15 minutes)     | 640,729 MB          |
| Human Genome (Uncompressed)                | 1.5 GB          |

Calculations and references-
1.  1 character is 1 byte
    https://www.unitconverters.net/data-storage/character-to-byte.htm
    2.  It is just multiplication on 1024x768 = 786432 pixcels the
        actual size of image is depends on the depth 16 bit or 32 bit.
        If we take 16 bit then sizi well be (1024x768x16
        bit)/(8*1024)/1024 = 1.5 MB
        https://jan.ucc.nau.edu/lrm22/pixels2bytes/calculator.htm
    3.  Raw image is 24 bit(3bytes). 1 Byte = 8bit. 1 MB = 1024KB,
        1KB=1024 Bytes ((1024 * 768 * 24 bit)) / ( 8 * 1024)) / 1024 =
        2.25 MB https://www.omnicalculator.com/other/image-file-size
    4.  https://www.circlehd.com/blog/how-to-calculate-video-file-size
        HEVC has compression ratio of 1000

    (1920 * 1080 * * 24 bit * 30 fps * 900 duration in seconds) =
    (1,343,692,800,000 / 8192) = (164,025,000 KB / 1024) = (160,180 MB /
    1000 = 160 MB

    5.  (1920 * 1080 * 24 bit * 30 fps * 900 duration in seconds) =
        (1,343,692,800,000 / 8192) = (164,025,000 KB / 1024) = 160,180
        MB
    6.  For 4K UHD, the dimensions is 3840 * 2160. So the size will be 4 times the HD video size. 160 * 4 =
        640MB
    7.  Row size 160,180 * 4 = 640,720 MB
    8. https://bitesizebio.com/8378/how-much-information-is-stored-in-the-human-genome/
       6*10^9 base pairs/diploid genome x 1 byte/4 base pairs = 1.5GB
  * 

#### b. Scaling

|                                           | Size     | # HD | 
|-------------------------------------------|---------:|-----:|
| Daily Twitter Tweets (Uncompressed)       | 64 GB |    1  |
| Daily Twitter Tweets (Snappy Compressed)  | 37.65 GB       |    1  |
| Daily Instagram Photos                    | 112.5     |   34   |
| Daily YouTube Videos                      | 460.8       |  139    |
| Yearly Twitter Tweets (Uncompressed)      | 23.36 TB       |  8    |
| Yearly Twitter Tweets (Snappy Compressed) | 13.74 TB       |   5   |
| Yearly Instagram Photos                   | 41 PB      |     12319 |
| Yearly YouTube Videos                     | 168.2 PB      |  50458    |

Calculations & References: Tweet size as 128 bytes
1. 
* 500,000,000 * 128 bytes = 64GB
* 64GB * 3(replicas)/(10 * 1024 GB) (tb per hd) = 1 HDD
2. 
* 64GB / 1.7 = 37.647GB
* 37.647 GB * 3 / (10 * 1024 GB) ( tb per HD) = 1 HDD
3. 
*  75 Million Photos * 1.5 MB PNG Image = 112.5 TB.
*  112.5 * 3(replicas)/10(tb per hd) = 33.75 HDD.
4. 
* 500hrs * 60mins = 30000mins. 15 min = 160MB, 30000mins = 320,000 MB. So we have 320GB per min. 320 * 60 * 24 = 460,800 GB.
* 460.8 * 3(replicas)/10(tb per hd) = 138.24 HDD
5. 
* 64 * 365 = 23360 GB.
* 23.36 * 3(replicas)/10(tb per hd) = 7.008
6. 
* 37.647 * 365 = 13741GB
* 13.74 * 3(replicas)/10(tb per hd) = 4.122
7. 
* 112.5 * 365 = 41062.5 TB
* 41062.5 * 3(replicas)/10(tb per hd) = 12318.75
8. 
* 460.8 * 365 = 168192 TB
* 168192 * 3(replicas)/10(tb per hd) = 50457.6

#### c. Reliability
|                                    | # HD | # Failures |
|------------------------------------|-----:|-----------:|
| Twitter Tweets (Uncompressed)      | 8  |   0.068         |
| Twitter Tweets (Snappy Compressed) | 5   |    0.0425        |
| Instagram Photos                   |12319|   104.7115         |
| YouTube Videos                     | 50458   |   428.893         |

Calculations & References:  
As per https://www.backblaze.com/b2/hard-drive-test-data.html Q1 2021
snapshot failure rate is 0.85% failures. So HD * Failure_Rate is our
failures result

1. 8 * 0.0085 = 0.068
2. 5 * 0.0085 = 0.0425
3. 12319 * 0.0085 = 104.7115
4. 50458 * 0.0085 = 428.893

#### d. Latency

|                           | One Way Latency      |
|---------------------------|---------------------:|
| Los Angeles to Amsterdam  | 139.193 ms                 |
| Low Earth Orbit Satellite | 600 ms                 |
| Geostationary Satellite   | 270 ms                 |
| Earth to the Moon         | 2.56 s                 |
| Earth to Mars             | 20 minutes            |

References-
Ping time between Los Angeles and Amsterdam ...https://wondernetwork.com › pings › Amsterdam
https://www.omniaccess.com/leo/#:~:text=The%20GEO%20latency%20is%20of,and%20an%20essential%20part%20if
https://www.satsig.net/latency.htm
https://mars.nasa.gov/mer/mission/timeline/surfaceops/navigation/#:~:text=Moving%20safely%20from%20rock%20to,about%2020%20minutes%20on%20average.

