# wob

Testing OCR of large and unsearchable PDF's from Dutch Public Access to Government Information Act ('Wob') using 
Tesseract Open Source OCR Engine (https://github.com/tesseract-ocr/tesseract). 

425 pages done in 15 minutes.

Input document: https://github.com/bertt/wob/blob/main/220211/wob-documenten.pdf (425 pages)

Sample page png: 

https://github.com/bertt/wob/blob/main/220211/images/wob-documenten-001.png

![image](https://user-images.githubusercontent.com/538812/154796646-3f30c3a6-020c-4034-8d61-9ac45a14e4af.png)

Result:

https://github.com/bertt/wob/blob/main/220211/images/wob-documenten-001.png.txt

```
App wisseling Gerard Beverdam (Nederlands Dagblad)

[09:08, 23-04-2020] Gerard Beverdam: Goedemorgen Anna Sophia, er is straks een gesprek van
minister Grapperhaus met de kerken. Kunnen wij na afloop over de inhoud contact hebben?

[14:54, 23-04-2020] Anna Sophia Posthumus: Dag Gerard, ik moet nog terugkoppeling krijgen
van het overleg. Bel je zo!

[14:55, 23-04-2020] Gerard Beverdam: **

0001 14826351
```

## Scripts

Step 1: Convert PDF to png's (each page 1 png)

```
$ pdftoppm wob-documenten.pdf ./images/wob-documenten -png
```

Step 2:

Loop through all png's, for each png do tesseract analysis, output txt files

```
echo "hallo"
cd images
for FILE in *.png; 
do echo $FILE; 
tesseract $FILE $FILE
done
```
