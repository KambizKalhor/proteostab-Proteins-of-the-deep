![ocean floor](/home/kkalhor/protein_stability_project/scientific_images/intro_title.png)

*STEEN'S LAB*\
codes by: kami

# Part one : diamond blast between two protein datasets
![diamond](/home/kkalhor/protein_stability_project/scientific_images/diamond.png)

###### learn more about diamond: https://manpages.ubuntu.com/manpages/focal/man1/diamond.1.html

step 1: download and install diamond


```bash
%%bash
# make a new working directory for balst using diamond
mkdir directory_for_diamond
cd directory_for_diamond
# downloading the diamond tool
wget http://github.com/bbuchfink/diamond/releases/download/v2.0.14/diamond-linux64.tar.gz
# decompressing 
tar xzf diamond-linux64.tar.gz
```

    URL transformed to HTTPS due to an HSTS policy
    --2023-02-07 17:29:12--  https://github.com/bbuchfink/diamond/releases/download/v2.0.14/diamond-linux64.tar.gz
    Resolving github.com (github.com)... 140.82.113.3
    Connecting to github.com (github.com)|140.82.113.3|:443... connected.
    HTTP request sent, awaiting response... 302 Found
    Location: https://objects.githubusercontent.com/github-production-release-asset-2e65be/31987083/718cf099-bab1-4005-88f2-dec24b5fbe7a?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20230207%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20230207T232913Z&X-Amz-Expires=300&X-Amz-Signature=2756f22be58026ae2b7847526323ea1adae12f60305008b655a9445501ae44f2&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=31987083&response-content-disposition=attachment%3B%20filename%3Ddiamond-linux64.tar.gz&response-content-type=application%2Foctet-stream [following]
    --2023-02-07 17:29:13--  https://objects.githubusercontent.com/github-production-release-asset-2e65be/31987083/718cf099-bab1-4005-88f2-dec24b5fbe7a?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20230207%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20230207T232913Z&X-Amz-Expires=300&X-Amz-Signature=2756f22be58026ae2b7847526323ea1adae12f60305008b655a9445501ae44f2&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=31987083&response-content-disposition=attachment%3B%20filename%3Ddiamond-linux64.tar.gz&response-content-type=application%2Foctet-stream
    Resolving objects.githubusercontent.com (objects.githubusercontent.com)... 185.199.108.133, 185.199.111.133, 185.199.110.133, ...
    Connecting to objects.githubusercontent.com (objects.githubusercontent.com)|185.199.108.133|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 13078995 (12M) [application/octet-stream]
    Saving to: ‘diamond-linux64.tar.gz’
    
         0K .......... .......... .......... .......... ..........  0% 1.95M 6s
        50K .......... .......... .......... .......... ..........  0% 2.66M 6s
       100K .......... .......... .......... .......... ..........  1% 9.36M 4s
       150K .......... .......... .......... .......... ..........  1% 11.7M 3s
       200K .......... .......... .......... .......... ..........  1% 3.96M 3s
       250K .......... .......... .......... .......... ..........  2% 17.9M 3s
       300K .......... .......... .......... .......... ..........  2% 14.7M 3s
       350K .......... .......... .......... .......... ..........  3% 19.4M 2s
       400K .......... .......... .......... .......... ..........  3% 18.6M 2s
       450K .......... .......... .......... .......... ..........  3% 5.56M 2s
       500K .......... .......... .......... .......... ..........  4% 33.1M 2s
       550K .......... .......... .......... .......... ..........  4% 22.0M 2s
       600K .......... .......... .......... .......... ..........  5% 38.6M 2s
       650K .......... .......... .......... .......... ..........  5% 35.7M 2s
       700K .......... .......... .......... .......... ..........  5% 27.2M 1s
       750K .......... .......... .......... .......... ..........  6% 41.6M 1s
       800K .......... .......... .......... .......... ..........  6% 35.9M 1s
       850K .......... .......... .......... .......... ..........  7% 49.9M 1s
       900K .......... .......... .......... .......... ..........  7% 50.5M 1s
       950K .......... .......... .......... .......... ..........  7% 49.5M 1s
      1000K .......... .......... .......... .......... ..........  8% 6.31M 1s
      1050K .......... .......... .......... .......... ..........  8% 40.4M 1s
      1100K .......... .......... .......... .......... ..........  9% 66.2M 1s
      1150K .......... .......... .......... .......... ..........  9% 32.6M 1s
      1200K .......... .......... .......... .......... ..........  9%  104M 1s
      1250K .......... .......... .......... .......... .......... 10% 48.1M 1s
      1300K .......... .......... .......... .......... .......... 10%  127M 1s
      1350K .......... .......... .......... .......... .......... 10% 61.0M 1s
      1400K .......... .......... .......... .......... .......... 11% 32.5M 1s
      1450K .......... .......... .......... .......... .......... 11% 99.4M 1s
      1500K .......... .......... .......... .......... .......... 12%  127M 1s
      1550K .......... .......... .......... .......... .......... 12% 65.5M 1s
      1600K .......... .......... .......... .......... .......... 12% 86.0M 1s
      1650K .......... .......... .......... .......... .......... 13% 86.6M 1s
      1700K .......... .......... .......... .......... .......... 13%  105M 1s
      1750K .......... .......... .......... .......... .......... 14% 67.8M 1s
      1800K .......... .......... .......... .......... .......... 14% 85.5M 1s
      1850K .......... .......... .......... .......... .......... 14%  131M 1s
      1900K .......... .......... .......... .......... .......... 15% 83.9M 1s
      1950K .......... .......... .......... .......... .......... 15% 90.6M 1s
      2000K .......... .......... .......... .......... .......... 16% 31.4M 1s
      2050K .......... .......... .......... .......... .......... 16% 7.94M 1s
      2100K .......... .......... .......... .......... .......... 16% 60.6M 1s
      2150K .......... .......... .......... .......... .......... 17%  117M 1s
      2200K .......... .......... .......... .......... .......... 17%  128M 1s
      2250K .......... .......... .......... .......... .......... 18%  107M 1s
      2300K .......... .......... .......... .......... .......... 18% 98.3M 1s
      2350K .......... .......... .......... .......... .......... 18% 64.3M 1s
      2400K .......... .......... .......... .......... .......... 19%  138M 1s
      2450K .......... .......... .......... .......... .......... 19%  126M 1s
      2500K .......... .......... .......... .......... .......... 19%  103M 1s
      2550K .......... .......... .......... .......... .......... 20% 94.8M 1s
      2600K .......... .......... .......... .......... .......... 20%  125M 1s
      2650K .......... .......... .......... .......... .......... 21%  127M 0s
      2700K .......... .......... .......... .......... .......... 21%  132M 0s
      2750K .......... .......... .......... .......... .......... 21% 90.9M 0s
      2800K .......... .......... .......... .......... .......... 22%  103M 0s
      2850K .......... .......... .......... .......... .......... 22%  128M 0s
      2900K .......... .......... .......... .......... .......... 23%  100M 0s
      2950K .......... .......... .......... .......... .......... 23%  119M 0s
      3000K .......... .......... .......... .......... .......... 23%  128M 0s
      3050K .......... .......... .......... .......... .......... 24%  101M 0s
      3100K .......... .......... .......... .......... .......... 24%  131M 0s
      3150K .......... .......... .......... .......... .......... 25% 90.3M 0s
      3200K .......... .......... .......... .......... .......... 25% 2.15M 0s
      3250K .......... .......... .......... .......... .......... 25%  190M 0s
      3300K .......... .......... .......... .......... .......... 26%  197M 0s
      3350K .......... .......... .......... .......... .......... 26%  178M 0s
      3400K .......... .......... .......... .......... .......... 27%  204M 0s
      3450K .......... .......... .......... .......... .......... 27%  185M 0s
      3500K .......... .......... .......... .......... .......... 27%  190M 0s
      3550K .......... .......... .......... .......... .......... 28%  168M 0s
      3600K .......... .......... .......... .......... .......... 28%  199M 0s
      3650K .......... .......... .......... .......... .......... 28%  191M 0s
      3700K .......... .......... .......... .......... .......... 29%  190M 0s
      3750K .......... .......... .......... .......... .......... 29%  164M 0s
      3800K .......... .......... .......... .......... .......... 30%  202M 0s
      3850K .......... .......... .......... .......... .......... 30%  199M 0s
      3900K .......... .......... .......... .......... .......... 30%  204M 0s
      3950K .......... .......... .......... .......... .......... 31%  173M 0s
      4000K .......... .......... .......... .......... .......... 31% 75.5M 0s
      4050K .......... .......... .......... .......... .......... 32%  181M 0s
      4100K .......... .......... .......... .......... .......... 32%  206M 0s
      4150K .......... .......... .......... .......... .......... 32%  204M 0s
      4200K .......... .......... .......... .......... .......... 33%  204M 0s
      4250K .......... .......... .......... .......... .......... 33%  174M 0s
      4300K .......... .......... .......... .......... .......... 34%  208M 0s
      4350K .......... .......... .......... .......... .......... 34%  176M 0s
      4400K .......... .......... .......... .......... .......... 34%  196M 0s
      4450K .......... .......... .......... .......... .......... 35%  179M 0s
      4500K .......... .......... .......... .......... .......... 35% 8.53M 0s
      4550K .......... .......... .......... .......... .......... 36%  181M 0s
      4600K .......... .......... .......... .......... .......... 36%  182M 0s
      4650K .......... .......... .......... .......... .......... 36%  158M 0s
      4700K .......... .......... .......... .......... .......... 37%  205M 0s
      4750K .......... .......... .......... .......... .......... 37% 75.7M 0s
      4800K .......... .......... .......... .......... .......... 37%  180M 0s
      4850K .......... .......... .......... .......... .......... 38%  195M 0s
      4900K .......... .......... .......... .......... .......... 38%  201M 0s
      4950K .......... .......... .......... .......... .......... 39%  144M 0s
      5000K .......... .......... .......... .......... .......... 39%  188M 0s
      5050K .......... .......... .......... .......... .......... 39%  183M 0s
      5100K .......... .......... .......... .......... .......... 40%  204M 0s
      5150K .......... .......... .......... .......... .......... 40%  160M 0s
      5200K .......... .......... .......... .......... .......... 41%  201M 0s
      5250K .......... .......... .......... .......... .......... 41%  176M 0s
      5300K .......... .......... .......... .......... .......... 41%  201M 0s
      5350K .......... .......... .......... .......... .......... 42%  187M 0s
      5400K .......... .......... .......... .......... .......... 42%  156M 0s
      5450K .......... .......... .......... .......... .......... 43%  199M 0s
      5500K .......... .......... .......... .......... .......... 43%  182M 0s
      5550K .......... .......... .......... .......... .......... 43%  172M 0s
      5600K .......... .......... .......... .......... .......... 44%  166M 0s
      5650K .......... .......... .......... .......... .......... 44%  202M 0s
      5700K .......... .......... .......... .......... .......... 45%  189M 0s
      5750K .......... .......... .......... .......... .......... 45%  202M 0s
      5800K .......... .......... .......... .......... .......... 45%  182M 0s
      5850K .......... .......... .......... .......... .......... 46%  197M 0s
      5900K .......... .......... .......... .......... .......... 46%  179M 0s
      5950K .......... .......... .......... .......... .......... 46%  195M 0s
      6000K .......... .......... .......... .......... .......... 47%  202M 0s
      6050K .......... .......... .......... .......... .......... 47%  204M 0s
      6100K .......... .......... .......... .......... .......... 48%  174M 0s
      6150K .......... .......... .......... .......... .......... 48%  204M 0s
      6200K .......... .......... .......... .......... .......... 48%  205M 0s
      6250K .......... .......... .......... .......... .......... 49% 12.4M 0s
      6300K .......... .......... .......... .......... .......... 49%  113M 0s
      6350K .......... .......... .......... .......... .......... 50%  103M 0s
      6400K .......... .......... .......... .......... .......... 50%  126M 0s
      6450K .......... .......... .......... .......... .......... 50%  130M 0s
      6500K .......... .......... .......... .......... .......... 51% 7.83M 0s
      6550K .......... .......... .......... .......... .......... 51%  117M 0s
      6600K .......... .......... .......... .......... .......... 52%  127M 0s
      6650K .......... .......... .......... .......... .......... 52%  128M 0s
      6700K .......... .......... .......... .......... .......... 52%  110M 0s
      6750K .......... .......... .......... .......... .......... 53%  106M 0s
      6800K .......... .......... .......... .......... .......... 53%  104M 0s
      6850K .......... .......... .......... .......... .......... 54%  129M 0s
      6900K .......... .......... .......... .......... .......... 54%  120M 0s
      6950K .......... .......... .......... .......... .......... 54%  108M 0s
      7000K .......... .......... .......... .......... .......... 55% 92.2M 0s
      7050K .......... .......... .......... .......... .......... 55%  123M 0s
      7100K .......... .......... .......... .......... .......... 55%  117M 0s
      7150K .......... .......... .......... .......... .......... 56%  107M 0s
      7200K .......... .......... .......... .......... .......... 56%  129M 0s
      7250K .......... .......... .......... .......... .......... 57% 92.2M 0s
      7300K .......... .......... .......... .......... .......... 57%  129M 0s
      7350K .......... .......... .......... .......... .......... 57%  114M 0s
      7400K .......... .......... .......... .......... .......... 58%  120M 0s
      7450K .......... .......... .......... .......... .......... 58%  125M 0s
      7500K .......... .......... .......... .......... .......... 59% 94.0M 0s
      7550K .......... .......... .......... .......... .......... 59%  111M 0s
      7600K .......... .......... .......... .......... .......... 59%  148M 0s
      7650K .......... .......... .......... .......... .......... 60%  106M 0s
      7700K .......... .......... .......... .......... .......... 60% 99.2M 0s
      7750K .......... .......... .......... .......... .......... 61% 90.7M 0s
      7800K .......... .......... .......... .......... .......... 61%  177M 0s
      7850K .......... .......... .......... .......... .......... 61% 93.8M 0s
      7900K .......... .......... .......... .......... .......... 62%  128M 0s
      7950K .......... .......... .......... .......... .......... 62%  125M 0s
      8000K .......... .......... .......... .......... .......... 63% 91.4M 0s
      8050K .......... .......... .......... .......... .......... 63%  126M 0s
      8100K .......... .......... .......... .......... .......... 63%  108M 0s
      8150K .......... .......... .......... .......... .......... 64%  124M 0s
      8200K .......... .......... .......... .......... .......... 64% 94.5M 0s
      8250K .......... .......... .......... .......... .......... 64%  125M 0s
      8300K .......... .......... .......... .......... .......... 65% 2.25M 0s
      8350K .......... .......... .......... .......... .......... 65%  183M 0s
      8400K .......... .......... .......... .......... .......... 66% 71.7M 0s
      8450K .......... .......... .......... .......... .......... 66%  119M 0s
      8500K .......... .......... .......... .......... .......... 66%  163M 0s
      8550K .......... .......... .......... .......... .......... 67% 96.1M 0s
      8600K .......... .......... .......... .......... .......... 67%  175M 0s
      8650K .......... .......... .......... .......... .......... 68% 54.7M 0s
      8700K .......... .......... .......... .......... .......... 68%  161M 0s
      8750K .......... .......... .......... .......... .......... 68% 20.9M 0s
      8800K .......... .......... .......... .......... .......... 69%  179M 0s
      8850K .......... .......... .......... .......... .......... 69%  193M 0s
      8900K .......... .......... .......... .......... .......... 70%  205M 0s
      8950K .......... .......... .......... .......... .......... 70%  174M 0s
      9000K .......... .......... .......... .......... .......... 70%  196M 0s
      9050K .......... .......... .......... .......... .......... 71%  202M 0s
      9100K .......... .......... .......... .......... .......... 71%  192M 0s
      9150K .......... .......... .......... .......... .......... 72%  183M 0s
      9200K .......... .......... .......... .......... .......... 72%  207M 0s
      9250K .......... .......... .......... .......... .......... 72%  210M 0s
      9300K .......... .......... .......... .......... .......... 73%  209M 0s
      9350K .......... .......... .......... .......... .......... 73%  173M 0s
      9400K .......... .......... .......... .......... .......... 73%  205M 0s
      9450K .......... .......... .......... .......... .......... 74%  209M 0s
      9500K .......... .......... .......... .......... .......... 74%  198M 0s
      9550K .......... .......... .......... .......... .......... 75%  180M 0s
      9600K .......... .......... .......... .......... .......... 75%  209M 0s
      9650K .......... .......... .......... .......... .......... 75%  209M 0s
      9700K .......... .......... .......... .......... .......... 76%  206M 0s
      9750K .......... .......... .......... .......... .......... 76%  178M 0s
      9800K .......... .......... .......... .......... .......... 77%  217M 0s
      9850K .......... .......... .......... .......... .......... 77%  189M 0s
      9900K .......... .......... .......... .......... .......... 77%  185M 0s
      9950K .......... .......... .......... .......... .......... 78%  207M 0s
     10000K .......... .......... .......... .......... .......... 78%  212M 0s
     10050K .......... .......... .......... .......... .......... 79%  183M 0s
     10100K .......... .......... .......... .......... .......... 79%  187M 0s
     10150K .......... .......... .......... .......... .......... 79%  209M 0s
     10200K .......... .......... .......... .......... .......... 80%  199M 0s
     10250K .......... .......... .......... .......... .......... 80%  209M 0s
     10300K .......... .......... .......... .......... .......... 81%  161M 0s
     10350K .......... .......... .......... .......... .......... 81%  207M 0s
     10400K .......... .......... .......... .......... .......... 81%  205M 0s
     10450K .......... .......... .......... .......... .......... 82%  201M 0s
     10500K .......... .......... .......... .......... .......... 82%  214M 0s
     10550K .......... .......... .......... .......... .......... 82%  179M 0s
     10600K .......... .......... .......... .......... .......... 83%  216M 0s
     10650K .......... .......... .......... .......... .......... 83%  214M 0s
     10700K .......... .......... .......... .......... .......... 84%  193M 0s
     10750K .......... .......... .......... .......... .......... 84%  190M 0s
     10800K .......... .......... .......... .......... .......... 84%  213M 0s
     10850K .......... .......... .......... .......... .......... 85%  213M 0s
     10900K .......... .......... .......... .......... .......... 85%  215M 0s
     10950K .......... .......... .......... .......... .......... 86%  176M 0s
     11000K .......... .......... .......... .......... .......... 86%  200M 0s
     11050K .......... .......... .......... .......... .......... 86%  212M 0s
     11100K .......... .......... .......... .......... .......... 87%  212M 0s
     11150K .......... .......... .......... .......... .......... 87%  212M 0s
     11200K .......... .......... .......... .......... .......... 88%  171M 0s
     11250K .......... .......... .......... .......... .......... 88%  212M 0s
     11300K .......... .......... .......... .......... .......... 88%  211M 0s
     11350K .......... .......... .......... .......... .......... 89%  213M 0s
     11400K .......... .......... .......... .......... .......... 89% 5.60M 0s
     11450K .......... .......... .......... .......... .......... 90%  125M 0s
     11500K .......... .......... .......... .......... .......... 90%  128M 0s
     11550K .......... .......... .......... .......... .......... 90% 85.1M 0s
     11600K .......... .......... .......... .......... .......... 91% 67.0M 0s
     11650K .......... .......... .......... .......... .......... 91%  129M 0s
     11700K .......... .......... .......... .......... .......... 91% 83.7M 0s
     11750K .......... .......... .......... .......... .......... 92% 84.0M 0s
     11800K .......... .......... .......... .......... .......... 92% 89.8M 0s
     11850K .......... .......... .......... .......... .......... 93%  107M 0s
     11900K .......... .......... .......... .......... .......... 93% 82.1M 0s
     11950K .......... .......... .......... .......... .......... 93% 95.8M 0s
     12000K .......... .......... .......... .......... .......... 94% 74.6M 0s
     12050K .......... .......... .......... .......... .......... 94%  102M 0s
     12100K .......... .......... .......... .......... .......... 95% 65.5M 0s
     12150K .......... .......... .......... .......... .......... 95%  131M 0s
     12200K .......... .......... .......... .......... .......... 95% 85.7M 0s
     12250K .......... .......... .......... .......... .......... 96% 84.4M 0s
     12300K .......... .......... .......... .......... .......... 96% 81.4M 0s
     12350K .......... .......... .......... .......... .......... 97%  126M 0s
     12400K .......... .......... .......... .......... .......... 97% 85.4M 0s
     12450K .......... .......... .......... .......... .......... 97% 79.9M 0s
     12500K .......... .......... .......... .......... .......... 98% 74.0M 0s
     12550K .......... .......... .......... .......... .......... 98% 86.0M 0s
     12600K .......... .......... .......... .......... .......... 99%  116M 0s
     12650K .......... .......... .......... .......... .......... 99% 84.7M 0s
     12700K .......... .......... .......... .......... .......... 99% 81.4M 0s
     12750K .......... .......... ..                              100%  178M=0.3s
    
    2023-02-07 17:29:13 (45.7 MB/s) - ‘diamond-linux64.tar.gz’ saved [13078995/13078995]
    


step 2: transfer your fasta dile to the same directory as diamond is\
here i made a combined fasta because i also want to blast my fasta file against itself


```bash
%%bash
# copy the two fasta files we want to perform diamond blast in our working directory
cp tylor_output_data/SRR7066492.faa directory_for_diamond/SRR7066492.faa
cp tylor_output_data/SRR7066493.faa directory_for_diamond/SRR7066493.faa
cat directory_for_diamond/SRR7066493.faa directory_for_diamond/SRR7066492.faa > directory_for_diamond/combined_SRR.faa
```

step 3: make reference for your blast\
here i made three references because i want to try every combination


```bash
%%bash
cd directory_for_diamond
# creating a diamond-formatted database file
./diamond makedb --in SRR7066493.faa -d SRR7066493_reference
./diamond makedb --in SRR7066492.faa -d SRR7066492_reference
./diamond makedb --in combined_SRR.faa -d combined_SRR_reference
```

    diamond v2.0.14.152 (C) Max Planck Society for the Advancement of Science
    Documentation, support and updates available at http://www.diamondsearch.org
    Please cite: http://dx.doi.org/10.1038/s41592-021-01101-x Nature Methods (2021)
    
    #CPU threads: 36
    Scoring parameters: (Matrix=BLOSUM62 Lambda=0.267 K=0.041 Penalties=11/1)
    Database input file: SRR7066493.faa
    Opening the database file...  [0s]
    Loading sequences...  [0.044s]
    Masking sequences...  [0.033s]
    Writing sequences...  [0.011s]
    Hashing sequences...  [0.004s]
    Loading sequences...  [0s]
    Writing trailer...  [0s]
    Closing the input file...  [0s]
    Closing the database file...  [0.002s]
    
    Database sequences  28154
      Database letters  7097417
         Database hash  71d2a4851354094218ec1b3638a861d1
            Total time  0.096000s
    diamond v2.0.14.152 (C) Max Planck Society for the Advancement of Science
    Documentation, support and updates available at http://www.diamondsearch.org
    Please cite: http://dx.doi.org/10.1038/s41592-021-01101-x Nature Methods (2021)
    
    #CPU threads: 36
    Scoring parameters: (Matrix=BLOSUM62 Lambda=0.267 K=0.041 Penalties=11/1)
    Database input file: SRR7066492.faa
    Opening the database file...  [0.037s]
    Loading sequences...  [0.018s]
    Masking sequences...  [0.016s]
    Writing sequences...  [0.002s]
    Hashing sequences...  [0.001s]
    Loading sequences...  [0s]
    Writing trailer...  [0s]
    Closing the input file...  [0s]
    Closing the database file...  [0.002s]
    
    Database sequences  7915
      Database letters  2177707
         Database hash  082e9236c3458cde25608b7b85c397c0
            Total time  0.078000s
    diamond v2.0.14.152 (C) Max Planck Society for the Advancement of Science
    Documentation, support and updates available at http://www.diamondsearch.org
    Please cite: http://dx.doi.org/10.1038/s41592-021-01101-x Nature Methods (2021)
    
    #CPU threads: 36
    Scoring parameters: (Matrix=BLOSUM62 Lambda=0.267 K=0.041 Penalties=11/1)
    Database input file: combined_SRR.faa
    Opening the database file...  [0s]
    Loading sequences...  [0.051s]
    Masking sequences...  [0.04s]
    Writing sequences...  [0.014s]
    Hashing sequences...  [0.005s]
    Loading sequences...  [0s]
    Writing trailer...  [0s]
    Closing the input file...  [0s]
    Closing the database file...  [0.001s]
    
    Database sequences  36069
      Database letters  9275124
         Database hash  8aa975aa33dd6c7a74e91552fe975f0f
            Total time  0.115000s


step 4: diamond blast main command\
i did every possible combination for query and reference


```bash
%%bash
cd directory_for_diamond
# use of of the commend below
# running a search in blastp mode because we have two .faa files
./diamond blastp -d SRR7066493_reference -q SRR7066492.faa -o matches_SRR7066493_as_reference.tsv --quiet
./diamond blastp -d SRR7066492_reference -q SRR7066493.faa -o matches_SRR7066492_as_reference.tsv --quiet
./diamond blastp -d combined_SRR_reference -q SRR7066493.faa -o matches_combined_SRR_as_reference93.tsv --quiet
./diamond blastp -d combined_SRR_reference -q SRR7066492.faa -o matches_combined_SRR_as_reference92.tsv --quiet
# other options include:
# running a search in blastx mode
###./diamond blastx -d reference -q reads.fasta -o matches.tsv

# or you can blast agains the downloaded database, here you dont need two .faa files and you blast your sequence against a database
# downloading and using a BLAST database
###update_blastdb.pl --decompress --blastdb_version 5 swissprot
###./diamond prepdb -d swissprot
###./diamond blastp -d swissprot -q queries.fasta -o matches.tsv
```

check point 1\
a glimpse on the initial data and number of matches


```bash
%%bash
cd directory_for_diamond
grep -c SRR7066492 SRR7066492.faa 
grep -c SRR7066493 SRR7066493.faa 
grep -c SRR7066493 matches_SRR7066492_as_reference.tsv 
grep -c SRR7066492 matches_SRR7066493_as_reference.tsv 
grep -c SRR7066492 matches_combined_SRR_as_reference92.tsv
grep -c SRR7066493 matches_combined_SRR_as_reference93.tsv
```

    7915
    28154
    382813
    162747
    173703
    600900


# what we understand about data in this part?
- we have 7915  proteins in SRR7066492 sample.
- we have 28154 proteins in SRR7066493 sample.

- when we diamond blast SRR7066493 sample against SRR7066492 sample we find 382813 matches.
- when we diamond blast SRR7066492 sample against SRR7066493 sample we find 162747 matches.

- when we diamond blast SRR7066492 sample against all sample (pool of SRR7066493 and SRR7066493) we find 173703 matches.
- when we diamond blast SRR7066493 sample against all sample (pool of SRR7066493 and SRR7066493) we find 600900 matches.

### what does it mean?
to me it means that:
1. we have proteins with mutiple matches
2. we have homolog proteins in same sample
   
so, let find out how many groups we have.
i choose the last blast result because it is the completest.(it has also lots of redundancy)


# PART TWO: Pythonic Probing: A Whimsical Dive into Oceanic Protein Data Analysis
![python](/home/kkalhor/protein_stability_project/scientific_images/python_logo.png)

# what bit-score and e-value is good in blast?

The Bit-Score and E-Value in BLAST (Basic Local Alignment Search Tool) are two measures that are used to evaluate the significance of a sequence alignment.

The Bit-Score is a log-based score that measures the strength of the alignment, with higher scores indicating a more significant match.

The E-Value is a statistical measure of the expectation of the number of matches at random that would have a Bit-Score equal to or greater than the one observed in the alignment. A lower E-Value indicates a more significant match, as it is less likely to have occurred by chance.

A good Bit-Score and E-Value depend on the context of the search and the desired level of sensitivity and specificity. Generally, a Bit-Score of 50 or higher and an E-Value of 1e-3 or lower are considered to be strong matches, while a Bit-Score of 30 or higher and an E-Value of 1e-5 or lower are considered to be significant matches. However, these thresholds can vary depending on the size and complexity of the database being searched and the length and similarity of the query sequence.

# what bit-score and e-value i choosed as my thereshold in my blast?
E-values equal or lower than 1e-5


step 1: importing data


```python
import pandas as pd
header_names = ["query_sequence_ID", "subject_sequence_ID", "pident", "length", "mismatch", "gapopen", "qstart", "qend", "sstart", "send", "E_value", "Bit_Score"]
df = pd.read_csv("directory_for_diamond/matches_combined_SRR_as_reference93.tsv", sep="\t",names=header_names)
```

### what are these header mean in diamond output? 
query_sequence_ID: The query sequence identifier.\
subject_sequence_ID: The subject sequence identifier.\
pident: The percentage of identical matches.\
length: The length of the alignment.\
mismatch: The number of mismatches in the alignment.\
gapopen: The number of gap openings in the alignment.\
qstart: The start position of the query sequence in the alignment.\
qend: The end position of the query sequence in the alignment.\
sstart: The start position of the subject sequence in the alignment.\
send: The end position of the subject sequence in the alignment.\
evalue: The expectation value of the alignment.\
bitscore: The Bit-Score of the alignment.\

the calculation below show that 28154 unique query_sequence_ID we have in our dataframe.\
it means that all the queries found a match in our reference and most of them have multiple matches.


```python
print('number of matched is:                  ', len(list(df['query_sequence_ID'])))
print('number of unique query_sequence_ID is: ', len(set(df['query_sequence_ID'])), '   which is equal to number of proteins in sample')

```

    number of matched is:                   600900
    number of unique query_sequence_ID is:  28154    which is equal to number of proteins in sample


step 2: now we should remove self matches using python code below:


```python
row_count_before_removing = df.shape[0]

df = df[df['query_sequence_ID'] != df['subject_sequence_ID']]

row_count_after_removing = df.shape[0]
number_of_removed_rows = row_count_before_removing - row_count_after_removing
print('we have had ',number_of_removed_rows, ' self matches which are now removed')

```

    we have had  28154  self matches which are now removed


step 3: now we should remove redundancies like when a --> b and b --> a


```python
import pandas as pd
import numpy as np

# compare elements in two columns and select the larger of the two # make two new sorted columns
df['compare1'] = np.where(df['query_sequence_ID'] > df['subject_sequence_ID'], df['query_sequence_ID'], df['subject_sequence_ID'])
df['compare2'] = np.where(df['subject_sequence_ID'] < df['query_sequence_ID'], df['subject_sequence_ID'], df['query_sequence_ID'])

# creat a new column which is cincatanated of two columns we made before
df['unique_code'] = df['compare1'] + df['compare2']

# now we are going to remove rows with similar 'unique_code' but first we sort them by E_values
df = df.sort_values(by='E_value')
df.drop_duplicates(subset='unique_code', inplace=True)

# now we need to remove the 2 extra columns we made later
df.drop('compare1', axis=1, inplace=True)
df.drop('compare2', axis=1, inplace=True)
```

step 4: checking the distribution of E-values

first lets plot the E_values


```python
import matplotlib.pyplot as plt

E_values = list(df['E_value'])

plt.hist(E_values, bins=100, edgecolor='black')
plt.xlabel('E-Values')
plt.ylabel('Frequency')
plt.title('distrbution of E-values')

plt.show()

```


    
![png](proteins_of_the_deep_files/proteins_of_the_deep_26_0.png)
    


- in histogram above you can see most matches have the E-value near Zero\
- the maximum E-value is 0.000999 and the minimum E-value is 0.0

in the analysis below you can see the quartiles of the E-values.


```python

import statistics
statistics.mean(E_values)
quartiles = statistics.quantiles(E_values, n=4)
print(quartiles)
```

    [6.4700000000000005e-75, 1.1299999999999999e-41, 4.32e-22]


step 5: here i will filter all the matches under my thereshold which is 1e-5

okay, so lets remove some of the rows with not enough good E-values, the threshold is 1e-5


```python
import pandas as pd

df = df[df['E_value'] <= 1e-5]

sets = list(zip(df['query_sequence_ID'], df['subject_sequence_ID']))

list_of_sets = []
for k in sets:
    list_of_sets.append(set(k))


```


```python
###### important ###### dont forget to remove this line kami
# for test
# list_of_sets = list_of_sets[0:1000]
```

step 6: time consuming categorizing step


```python
# we perform this function to union the sets that have intersection
def if_intersection_then_union(set1, set2):
    if set1.intersection(set2):
        union = set1 | set2
    else:
        union = {}
    return union


# we perform the next code to remove duplicated sets
# input of function is a list of sets and this code removes the duplicated sets in our list
def remove_duplicated_sets(list_of_sets):
    unique_list = set()
    for s in list_of_sets:
        unique_list.add(frozenset(s))

    unique_list = [set(s) for s in unique_list]
    return unique_list

# this function is the combination of two above functions
def categorizing_proteins(list_of_sets):
    the_range = len(list_of_sets)
    for i in range(0,the_range):
        for j in range(0,the_range):
            union = if_intersection_then_union(list_of_sets[i], list_of_sets[j])
            if union != {}:
                list_of_sets[i] = union
                list_of_sets[j] = union
    list_of_sets = remove_duplicated_sets(list_of_sets)
    return list_of_sets


# this next code is REALLY time consuming so we break it to multiple tasks
# list_of_sets = categorizing_proteins(list_of_sets)

```

this step is performed just to reduce the computational costs


```python


def make_small_first_then(slice_length, list_of_sets):
    sub_list_of_sets = []
    # this should change to 10000
    for slice_index in range (0,len(list_of_sets)):
        if slice_index%slice_length == 0:
            start = slice_index
            end = slice_index + slice_length
            sub_list_of_sets = sub_list_of_sets + categorizing_proteins(list_of_sets[start:end])

    print('lenght of sublist is: ', len(sub_list_of_sets))
    return sub_list_of_sets


```


```python
import random
for i in range(0,10000000):
    sub_list_of_sets = make_small_first_then(1000,list_of_sets)
    if len(list_of_sets) == len(sub_list_of_sets):
        break
    list_of_sets = sub_list_of_sets
    sub_list_of_sets = random.shuffle(sub_list_of_sets)
```

    lenght of sublist is:  339393
    lenght of sublist is:  305492
    lenght of sublist is:  272347
    lenght of sublist is:  240108
    lenght of sublist is:  208779
    lenght of sublist is:  178389
    lenght of sublist is:  148931
    lenght of sublist is:  121086
    lenght of sublist is:  95728
    lenght of sublist is:  73036
    lenght of sublist is:  53461
    lenght of sublist is:  37472
    lenght of sublist is:  24630
    lenght of sublist is:  14892
    lenght of sublist is:  7985
    lenght of sublist is:  3718
    lenght of sublist is:  1445
    lenght of sublist is:  528
    lenght of sublist is:  224
    lenght of sublist is:  224


at last step we want to perform the last set making\
again this step will be time consuming and we have to do it!\
i tried so many ways but failed


```python
list_of_sets = categorizing_proteins(list_of_sets)
```

now we need to save the result as pickle list


```python
import pickle
# save the list to a file
with open("directory_for_diamond/smallest_list_of_setss_10e5.pickle", "wb") as f:
    pickle.dump(list_of_sets, f)
```


```python
import pickle
# later, you can load the list from the file
with open("directory_for_diamond/smallest_list_of_setss_10e5.pickle", "rb") as f:
    list_of_sets = pickle.load(f)
```

now let have some analysis


```python
lenghts_list = []
for i in list_of_sets:
    lenghts_list.append(len(i))

import matplotlib.pyplot as plt


plt.hist(lenghts_list, bins=500, edgecolor='black')
plt.xlabel('groups')
plt.ylabel('Frequency')
plt.title('Frequency of members of a group in List')
plt.xlim(0, 1000)  # specify the desired x-axis range
plt.show()

```


    
![png](proteins_of_the_deep_files/proteins_of_the_deep_44_0.png)
    


in this code you can see, most of groups are couple proteins (i mean two similar proteins)


```python
import statistics


print('minimum is : ' , min(lenghts_list))
quartiles = statistics.quantiles(lenghts_list, n=4)
print('first quartile is: ', quartiles[0])
print('median is: ', statistics.median(lenghts_list))
print('third quartile is: ', quartiles[2])
print('maximum is : ' , max(lenghts_list))
```

    minimum is :  2
    first quartile is:  2.0
    median is:  4.0
    third quartile is:  15.0
    maximum is :  27241


in this code we want to see frequency of protein sets lenght


```python
frequency_dict = {}
for item in lenghts_list:
    if item in frequency_dict:
        frequency_dict[item] += 1
    else:
        frequency_dict[item] = 1

sorted_dict = sorted(frequency_dict.items(), key=lambda x: x[0])
print(sorted_dict)

```

    [(2, 68), (3, 40), (4, 14), (5, 13), (6, 7), (7, 7), (8, 5), (10, 2), (11, 4), (12, 2), (13, 2), (14, 3), (15, 2), (19, 4), (20, 1), (21, 1), (22, 1), (23, 1), (24, 1), (28, 1), (29, 2), (36, 1), (38, 1), (39, 1), (43, 2), (46, 1), (47, 1), (50, 1), (53, 1), (60, 1), (75, 1), (76, 2), (79, 1), (81, 1), (85, 1), (93, 1), (97, 1), (109, 2), (118, 1), (130, 1), (135, 1), (139, 1), (152, 1), (158, 1), (159, 1), (175, 1), (193, 1), (201, 1), (204, 1), (216, 1), (247, 1), (248, 1), (251, 1), (262, 1), (306, 1), (314, 1), (316, 1), (463, 1), (512, 1), (792, 1), (27241, 1)]


this plot shows


```python
import matplotlib.pyplot as plt


x = list(frequency_dict.keys())
y = list(frequency_dict.values())

plt.scatter(x, y)
plt.xlabel("Element")
plt.ylabel("Frequency")
plt.title("Frequency of Elements in a List")
plt.show()

```


    
![png](proteins_of_the_deep_files/proteins_of_the_deep_50_0.png)
    


let zoom into this plot and see what is there clearly


```python
#remove values highr than
high_limit = 100

frequency_dict_zoom = {k: v for k, v in frequency_dict.items() if k <= high_limit}


import matplotlib.pyplot as plt


x = list(frequency_dict_zoom.keys())
y = list(frequency_dict_zoom.values())

plt.scatter(x, y)
plt.xlabel("Element")
plt.ylabel("Frequency")
plt.title("Frequency of Elements in a List")
plt.show()

```


    
![png](proteins_of_the_deep_files/proteins_of_the_deep_52_0.png)
    


now lets see if any set is a single protein family or not( it should be )


```python
list_of_sets[43]
```




    {'SRR7066493_k141_1796872_1',
     'SRR7066493_k141_1972148_1',
     'SRR7066493_k141_3161307_1',
     'SRR7066493_k141_3246752_2'}




```python
a_set = list(list_of_sets[43])



import pandas as pd

SRR = 'SRR7066493'
#the wired thing is that we have two dbCAN output files and one of them is bigger
# using SRR7066493_dbcan_p.tsv
df = pd.read_csv('tylor_output_data/' + SRR+ '_dbcan.tsv', sep='\t', names=['family', 'column2', 'sequence', 'column4', 'column5', 'column6', 'column7', 'column8', 'column9', 'column10' ])
# using SRR7066493_dbcan.tsv
#df = pd.read_csv('tylor_output_data/' + SRR+ '_dbcan_p.tsv', sep='\t', names=['family', 'sequence'])

# print(df)


df = df[df['sequence'].isin(a_set)]
main_df = df

df = df['family']
# function to remove numbers from categories
def remove_numbers(string):
    string = string.replace('.hmm','')
    return ''.join(c for c in string if not c.isdigit())


main_gene_families_list = []
for gene_family in df:
    gene_family = remove_numbers(gene_family).replace('_',' ')
    if str(gene_family)[-1] == ' ':
        gene_family = gene_family[0:-1]
    main_gene_families_list.append(gene_family)


# frequency of main gene families
def count_frequency(lst):
    frequency = {}
    for item in lst:
        if item in frequency:
            frequency[item] += 1
        else:
            frequency[item] = 1
    return frequency

lst = main_gene_families_list
frequency_dict = count_frequency(lst)


def sort_dict_by_value(dictionary):
    return {k: v for k, v in sorted(dictionary.items(), key=lambda item: item[1],reverse=True)}

frequency_dict = sort_dict_by_value(frequency_dict)
for key, value in frequency_dict.items():
    print(f"{key} appears {value} times")
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-8-39e5c8e91959> in <module>
    ----> 1 a_set = list(list_of_sets[43])
          2 
          3 
          4 
          5 import pandas as pd


    NameError: name 'list_of_sets' is not defined



```python
len(list_of_sets)
```




    224




```python

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>family</th>
      <th>column2</th>
      <th>sequence</th>
      <th>column4</th>
      <th>column5</th>
      <th>column6</th>
      <th>column7</th>
      <th>column8</th>
      <th>column9</th>
      <th>column10</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>GH24.hmm</td>
      <td>137</td>
      <td>SRR7066492_k141_1000132_1</td>
      <td>110</td>
      <td>3.300000e-19</td>
      <td>3</td>
      <td>109</td>
      <td>3</td>
      <td>108</td>
      <td>0.773723</td>
    </tr>
    <tr>
      <th>1</th>
      <td>GH43_22.hmm</td>
      <td>209</td>
      <td>SRR7066492_k141_1000153_1</td>
      <td>120</td>
      <td>3.900000e-19</td>
      <td>51</td>
      <td>152</td>
      <td>1</td>
      <td>94</td>
      <td>0.483254</td>
    </tr>
    <tr>
      <th>2</th>
      <td>PL35.hmm</td>
      <td>179</td>
      <td>SRR7066492_k141_1000179_1</td>
      <td>78</td>
      <td>1.100000e-21</td>
      <td>100</td>
      <td>174</td>
      <td>3</td>
      <td>77</td>
      <td>0.413408</td>
    </tr>
    <tr>
      <th>3</th>
      <td>PL35.hmm</td>
      <td>179</td>
      <td>SRR7066492_k141_1000179_2</td>
      <td>133</td>
      <td>1.400000e-39</td>
      <td>2</td>
      <td>83</td>
      <td>50</td>
      <td>133</td>
      <td>0.452514</td>
    </tr>
    <tr>
      <th>4</th>
      <td>GH29.hmm</td>
      <td>346</td>
      <td>SRR7066492_k141_100023_1</td>
      <td>210</td>
      <td>1.700000e-37</td>
      <td>109</td>
      <td>264</td>
      <td>2</td>
      <td>153</td>
      <td>0.447977</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>28376</th>
      <td>CE19.hmm</td>
      <td>332</td>
      <td>SRR7066493_k141_999384_1</td>
      <td>153</td>
      <td>2.300000e-39</td>
      <td>145</td>
      <td>288</td>
      <td>1</td>
      <td>151</td>
      <td>0.430723</td>
    </tr>
    <tr>
      <th>28377</th>
      <td>GT51.hmm</td>
      <td>177</td>
      <td>SRR7066493_k141_999426_1</td>
      <td>135</td>
      <td>4.400000e-23</td>
      <td>112</td>
      <td>177</td>
      <td>1</td>
      <td>66</td>
      <td>0.367232</td>
    </tr>
    <tr>
      <th>28378</th>
      <td>GH168.hmm</td>
      <td>277</td>
      <td>SRR7066493_k141_999614_1</td>
      <td>188</td>
      <td>5.400000e-52</td>
      <td>108</td>
      <td>277</td>
      <td>1</td>
      <td>170</td>
      <td>0.610108</td>
    </tr>
    <tr>
      <th>28379</th>
      <td>GT2_Glycos_transf_2.hmm</td>
      <td>170</td>
      <td>SRR7066493_k141_999669_1</td>
      <td>170</td>
      <td>3.500000e-23</td>
      <td>1</td>
      <td>157</td>
      <td>9</td>
      <td>166</td>
      <td>0.917647</td>
    </tr>
    <tr>
      <th>28380</th>
      <td>GT2_Glycos_transf_2.hmm</td>
      <td>170</td>
      <td>SRR7066493_k141_999875_1</td>
      <td>113</td>
      <td>8.300000e-30</td>
      <td>1</td>
      <td>101</td>
      <td>9</td>
      <td>112</td>
      <td>0.588235</td>
    </tr>
  </tbody>
</table>
<p>36394 rows × 10 columns</p>
</div>




```python
for i in range(0,224):
    a_set = list(list_of_sets[i])
    print(i)


    import pandas as pd

    SRR = 'SRR7066493'
    #the wired thing is that we have two dbCAN output files and one of them is bigger
    # using SRR7066493_dbcan_p.tsv
    df1 = pd.read_csv('tylor_output_data/' + 'SRR7066492'+ '_dbcan.tsv', sep='\t', names=['family', 'column2', 'sequence', 'column4', 'column5', 'column6', 'column7', 'column8', 'column9', 'column10' ])
    df2 = pd.read_csv('tylor_output_data/' + 'SRR7066493'+ '_dbcan.tsv', sep='\t', names=['family', 'column2', 'sequence', 'column4', 'column5', 'column6', 'column7', 'column8', 'column9', 'column10' ])
    df = pd.concat([df1, df2])
    # using SRR7066493_dbcan.tsv
    #df = pd.read_csv('tylor_output_data/' + SRR+ '_dbcan_p.tsv', sep='\t', names=['family', 'sequence'])

    # print(df)


    df = df[df['sequence'].isin(a_set)]
    main_df = df

    df = df['family']
    # function to remove numbers from categories
    def remove_numbers(string):
        string = string.replace('.hmm','')
        return ''.join(c for c in string if not c.isdigit())


    main_gene_families_list = []
    for gene_family in df:
        gene_family = remove_numbers(gene_family).replace('_',' ')
        if str(gene_family)[-1] == ' ':
            gene_family = gene_family[0:-1]
        main_gene_families_list.append(gene_family)


    # frequency of main gene families
    def count_frequency(lst):
        frequency = {}
        for item in lst:
            if item in frequency:
                frequency[item] += 1
            else:
                frequency[item] = 1
        return frequency

    lst = main_gene_families_list
    frequency_dict = count_frequency(lst)


    def sort_dict_by_value(dictionary):
        return {k: v for k, v in sorted(dictionary.items(), key=lambda item: item[1],reverse=True)}

    frequency_dict = sort_dict_by_value(frequency_dict)
    for key, value in frequency_dict.items():
        print(f"{key} appears {value} times")

    print('+++++++++++++++++++++++++++++++')
    print('===============================')
```

    0
    GH appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    1
    GH appears 7 times
    +++++++++++++++++++++++++++++++
    ===============================
    2
    GT appears 15 times
    +++++++++++++++++++++++++++++++
    ===============================
    3
    GH appears 135 times
    +++++++++++++++++++++++++++++++
    ===============================
    4
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    5
    GT appears 39 times
    +++++++++++++++++++++++++++++++
    ===============================
    6
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    7
    GT appears 6 times
    +++++++++++++++++++++++++++++++
    ===============================
    8
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    9
    GH appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    10
    GT appears 5 times
    +++++++++++++++++++++++++++++++
    ===============================
    11
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    12
    GT appears 159 times
    +++++++++++++++++++++++++++++++
    ===============================
    13
    CBM appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    14
    PL appears 11 times
    +++++++++++++++++++++++++++++++
    ===============================
    15
    GT appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    16
    GH appears 36 times
    +++++++++++++++++++++++++++++++
    ===============================
    17
    GT appears 28 times
    +++++++++++++++++++++++++++++++
    ===============================
    18
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    19
    GT appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    20
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    21
    GH appears 110 times
    +++++++++++++++++++++++++++++++
    ===============================
    22
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    23
    PL appears 11 times
    +++++++++++++++++++++++++++++++
    ===============================
    24
    CE appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    25
    GH appears 8 times
    +++++++++++++++++++++++++++++++
    ===============================
    26
    CE appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    27
    CBM appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    28
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    29
    GT appears 5 times
    +++++++++++++++++++++++++++++++
    ===============================
    30
    GT appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    31
    GH appears 6 times
    +++++++++++++++++++++++++++++++
    ===============================
    32
    GH appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    33
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    34
    CBM appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    35
    GT appears 10 times
    +++++++++++++++++++++++++++++++
    ===============================
    36
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    37
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    38
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    39
    GT appears 201 times
    +++++++++++++++++++++++++++++++
    ===============================
    40
    GT appears 5 times
    +++++++++++++++++++++++++++++++
    ===============================
    41
    GH appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    42
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    43
    GT appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    44
    CBM appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    45
    PL appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    46
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    47
    CE appears 7 times
    +++++++++++++++++++++++++++++++
    ===============================
    48
    CE appears 306 times
    +++++++++++++++++++++++++++++++
    ===============================
    49
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    50
    PL appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    51
    GH appears 43 times
    +++++++++++++++++++++++++++++++
    ===============================
    52
    AA appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    53
    GH appears 6 times
    +++++++++++++++++++++++++++++++
    ===============================
    54
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    55
    CBM appears 13 times
    GH appears 1 times
    +++++++++++++++++++++++++++++++
    ===============================
    56
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    57
    PL appears 11 times
    +++++++++++++++++++++++++++++++
    ===============================
    58
    GH appears 5 times
    +++++++++++++++++++++++++++++++
    ===============================
    59
    CE appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    60
    GH appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    61
    GT appears 46 times
    +++++++++++++++++++++++++++++++
    ===============================
    62
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    63
    GT appears 29 times
    +++++++++++++++++++++++++++++++
    ===============================
    64
    GH appears 12 times
    +++++++++++++++++++++++++++++++
    ===============================
    65
    CBM appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    66
    GH appears 139 times
    +++++++++++++++++++++++++++++++
    ===============================
    67
    GT appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    68
    GT appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    69
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    70
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    71
    GT appears 247 times
    +++++++++++++++++++++++++++++++
    ===============================
    72
    GT appears 81 times
    +++++++++++++++++++++++++++++++
    ===============================
    73
    CBM appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    74
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    75
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    76
    PL appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    77
    GT appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    78
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    79
    CE appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    80
    CBM appears 5 times
    +++++++++++++++++++++++++++++++
    ===============================
    81
    AA appears 204 times
    +++++++++++++++++++++++++++++++
    ===============================
    82
    PL appears 63 times
    CBM appears 15 times
    +++++++++++++++++++++++++++++++
    ===============================
    83
    GH appears 7 times
    +++++++++++++++++++++++++++++++
    ===============================
    84
    CE appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    85
    GT appears 6 times
    +++++++++++++++++++++++++++++++
    ===============================
    86
    GT Glyco tranf  appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    87
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    88
    CBM appears 8 times
    +++++++++++++++++++++++++++++++
    ===============================
    89
    GH appears 70 times
    CBM appears 6 times
    +++++++++++++++++++++++++++++++
    ===============================
    90
    GH appears 19 times
    +++++++++++++++++++++++++++++++
    ===============================
    91
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    92
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    93
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    94
    GT appears 29 times
    +++++++++++++++++++++++++++++++
    ===============================
    95
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    96
    GH appears 118 times
    +++++++++++++++++++++++++++++++
    ===============================
    97
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    98
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    99
    GH appears 152 times
    +++++++++++++++++++++++++++++++
    ===============================
    100
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    101
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    102
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    103
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    104
    GH appears 53 times
    +++++++++++++++++++++++++++++++
    ===============================
    105
    GH appears 15 times
    +++++++++++++++++++++++++++++++
    ===============================
    106
    GT appears 19 times
    +++++++++++++++++++++++++++++++
    ===============================
    107
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    108
    GH appears 5 times
    +++++++++++++++++++++++++++++++
    ===============================
    109
    GT appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    110
    CE appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    111
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    112
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    113
    PL appears 23 times
    +++++++++++++++++++++++++++++++
    ===============================
    114
    GH appears 11 times
    +++++++++++++++++++++++++++++++
    ===============================
    115
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    116
    GT appears 314 times
    +++++++++++++++++++++++++++++++
    ===============================
    117
    GH appears 43 times
    +++++++++++++++++++++++++++++++
    ===============================
    118
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    119
    GH appears 38 times
    +++++++++++++++++++++++++++++++
    ===============================
    120
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    121
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    122
    GT appears 6 times
    +++++++++++++++++++++++++++++++
    ===============================
    123
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    124
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    125
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    126
    GT appears 47 times
    +++++++++++++++++++++++++++++++
    ===============================
    127
    GT appears 512 times
    +++++++++++++++++++++++++++++++
    ===============================
    128
    GT appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    129
    GH appears 791 times
    CBM appears 1 times
    +++++++++++++++++++++++++++++++
    ===============================
    130
    AA appears 5 times
    +++++++++++++++++++++++++++++++
    ===============================
    131
    GH appears 5 times
    +++++++++++++++++++++++++++++++
    ===============================
    132
    GT appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    133
    GT Glyco tranf  appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    134
    GH appears 216 times
    +++++++++++++++++++++++++++++++
    ===============================
    135
    GH appears 6 times
    +++++++++++++++++++++++++++++++
    ===============================
    136
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    137
    CBM appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    138
    GH appears 55 times
    GT appears 45 times
    +++++++++++++++++++++++++++++++
    ===============================
    139
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    140
    GT appears 19 times
    +++++++++++++++++++++++++++++++
    ===============================
    141
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    142
    GT appears 14 times
    +++++++++++++++++++++++++++++++
    ===============================
    143
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    144
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    145
    GT Glyco tranf  appears 6 times
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    146
    GT appears 19 times
    +++++++++++++++++++++++++++++++
    ===============================
    147
    CE appears 12 times
    +++++++++++++++++++++++++++++++
    ===============================
    148
    GH appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    149
    CBM appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    150
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    151
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    152
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    153
    PL appears 7 times
    +++++++++++++++++++++++++++++++
    ===============================
    154
    GH appears 175 times
    +++++++++++++++++++++++++++++++
    ===============================
    155
    GT appears 132 times
    +++++++++++++++++++++++++++++++
    ===============================
    156
    CE appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    157
    GT appears 6 times
    +++++++++++++++++++++++++++++++
    ===============================
    158
    GT appears 50 times
    +++++++++++++++++++++++++++++++
    ===============================
    159
    GT appears 8 times
    +++++++++++++++++++++++++++++++
    ===============================
    160
    CE appears 7 times
    +++++++++++++++++++++++++++++++
    ===============================
    161
    GH appears 88 times
    +++++++++++++++++++++++++++++++
    ===============================
    162
    CE appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    163
    CBM appears 2 times
    GH appears 1 times
    +++++++++++++++++++++++++++++++
    ===============================
    164
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    165
    GH appears 109 times
    +++++++++++++++++++++++++++++++
    ===============================
    166
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    167
    GH appears 5 times
    +++++++++++++++++++++++++++++++
    ===============================
    168
    GH appears 12614 times
    GT appears 6207 times
    GT Glycos transf appears 4120 times
    CE appears 1650 times
    CBM appears 1406 times
    PL appears 1327 times
    GT Glyco tranf  appears 172 times
    GT Glyco trans  appears 50 times
    +++++++++++++++++++++++++++++++
    ===============================
    169
    CE appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    170
    CE appears 316 times
    +++++++++++++++++++++++++++++++
    ===============================
    171
    GH appears 79 times
    +++++++++++++++++++++++++++++++
    ===============================
    172
    GH appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    173
    GT appears 249 times
    +++++++++++++++++++++++++++++++
    ===============================
    174
    GT appears 14 times
    +++++++++++++++++++++++++++++++
    ===============================
    175
    PL appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    176
    GH appears 463 times
    +++++++++++++++++++++++++++++++
    ===============================
    177
    CE appears 14 times
    +++++++++++++++++++++++++++++++
    ===============================
    178
    GH appears 59 times
    CBM appears 1 times
    +++++++++++++++++++++++++++++++
    ===============================
    179
    PL appears 7 times
    +++++++++++++++++++++++++++++++
    ===============================
    180
    GT appears 24 times
    +++++++++++++++++++++++++++++++
    ===============================
    181
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    182
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    183
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    184
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    185
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    186
    PL appears 5 times
    +++++++++++++++++++++++++++++++
    ===============================
    187
    GH appears 158 times
    +++++++++++++++++++++++++++++++
    ===============================
    188
    GT appears 5 times
    +++++++++++++++++++++++++++++++
    ===============================
    189
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    190
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    191
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    192
    GT appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    193
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    194
    AA appears 262 times
    +++++++++++++++++++++++++++++++
    ===============================
    195
    GH appears 13 times
    +++++++++++++++++++++++++++++++
    ===============================
    196
    GT appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    197
    GH appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    198
    CBM appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    199
    GH appears 8 times
    +++++++++++++++++++++++++++++++
    ===============================
    200
    GT appears 22 times
    +++++++++++++++++++++++++++++++
    ===============================
    201
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    202
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    203
    CE appears 251 times
    +++++++++++++++++++++++++++++++
    ===============================
    204
    PL appears 20 times
    +++++++++++++++++++++++++++++++
    ===============================
    205
    GT appears 193 times
    +++++++++++++++++++++++++++++++
    ===============================
    206
    GT appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    207
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    208
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    209
    CE appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    210
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    211
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    212
    AA appears 11 times
    +++++++++++++++++++++++++++++++
    ===============================
    213
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    214
    GH appears 93 times
    +++++++++++++++++++++++++++++++
    ===============================
    215
    GH appears 5 times
    +++++++++++++++++++++++++++++++
    ===============================
    216
    GH appears 76 times
    +++++++++++++++++++++++++++++++
    ===============================
    217
    GH appears 3 times
    +++++++++++++++++++++++++++++++
    ===============================
    218
    AA appears 21 times
    +++++++++++++++++++++++++++++++
    ===============================
    219
    GH appears 4 times
    +++++++++++++++++++++++++++++++
    ===============================
    220
    GH appears 5 times
    +++++++++++++++++++++++++++++++
    ===============================
    221
    GH appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    222
    GT appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================
    223
    GH appears 5 times
    CBM appears 2 times
    +++++++++++++++++++++++++++++++
    ===============================



```python
list_of_sets[223]
```




    {'SRR7066492_k141_180964_1',
     'SRR7066493_k141_1229800_1',
     'SRR7066493_k141_2187722_1',
     'SRR7066493_k141_2798256_1',
     'SRR7066493_k141_2852300_1',
     'SRR7066493_k141_3057455_2',
     'SRR7066493_k141_812894_1'}



SRR7066492_k141_180964_1 --> SRR7066493_k141_3057455_2 , #SRR7066493_k141_2187722_1

SRR7066493_k141_1229800_1 --> SRR7066493_k141_812894_1 ,   ##SRR7066493_k141_2852300_1

SRR7066493_k141_2798256_1 --> #SRR7066493_k141_2187722_1 , ##SRR7066493_k141_2852300_1


```bash
%%bash
cd tylor_output_data
cat SRR7066492_dbcan.tsv SRR7066493_dbcan.tsv > combined_file.tsv
# grep SRR7066492_k141_180964_1 combined_file.tsv
# grep SRR7066493_k141_3057455_2 combined_file.tsv
# grep SRR7066493_k141_2187722_1 combined_file.tsv
# grep SRR7066493_k141_2852300_1 combined_file.tsv
# grep SRR7066493_k141_2798256_1 combined_file.tsv


# grep SRR7066493_k141_1229800_1 combined_file.tsv
# grep SRR7066493_k141_812894_1 combined_file.tsv

rm combined_file.tsv
```

    CBM35.hmm	119	SRR7066493_k141_1229800_1	380	4.8e-30	2	119	145	259	0.983193277310924


# finally

how can two proteins from two families be together in a blast?????
it took nearly three days for me to find it!!!!!!!
