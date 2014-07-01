baseline-mgr
============


> Written by [Wayne Roddy](wayne@modx.com). June 19, 2014


###Cloud & Compass Setup

1. Open a ticket from the MODX Cloud Dashboard, by clicking the Green “Help” button.  
  - Question: Sassify Me
  - Details:  I'm ready to create a NEW manager theme.
  
2. Wait for your Ticket Reply

---

###Theme Folder Setup

1. Download the Baseline Repo from [GitHub](https://github.com/modxcms/baseline-mgr)
2. Zip the theme folder you want to install
3. SSH into your site using the credentials from your Dashboard. Change **c1286** to your cloud number

  `ssh c1286@paas1.tx.modxcloud.com`

 - Say Yes to continue connecting (if prompted)
 - Enter the cloud SSH password

4. Duplicate the "default" folder - Example name is "baseline"
 
  `cp -r www/manager/templates/default www/manager/templates/baseline`

5. From a new Terminal Window - upload the theme folder you Zipped. Below is just an example.

  ```scp ~/Downloads/baseline-mgr-master/baseline.zip c1286@paas1.tx.modxcloud.com:/home/www/manager/templates/baseline```

6. Back to your SSH Cloud Server Terminal Window - Go to the Template Folder
```
cd www/manager/templates/baseline
unzip baseline.zip
mkdir sass/
mv baseline/sass/* sass/
```

---

###Set your Compass

1. Create your compass setup:
```
compass create --bare --sass-dir "sass" --css-dir "css" --images-dir "images"
```
2. Make sure you get "Congratulations"
3. Type `compass watch`
3. You should see it compile SASS and create **index.css** with the notification `Compass is polling for changes. Press Ctrl-C to Stop.`

---

###Turn on New Theme

1. Login to the Manager
2. Go to System Settings
3. "Filter by Area" -> Back-end Manager
4. Scroll Down to "Manager Theme" and choose your theme
