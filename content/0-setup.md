---
title: Setup
nav: true
---
# Setup

-----

## Download & install software
{% capture text %}
- Check that you have Firefox or Chrome browsers installed and set as your default browser. OpenRefine runs in your default browser. It will not run correctly in Internet Explorer.
- Download the latest software version from [http://openrefine.org](http://openrefine.org). 
- Unzip the downloaded file into a directory by right-clicking and selecting `Extract ...`.   Name that directory something like OpenRefine.
- Go to your newly created OpenRefine directory.
- Move the folder to `c:\program files` (you may need administrator privileges to do this)
- Launch OpenRefine by clicking the `openrefine.exe` file (this will launch a command prompt window, but you can ignore that and wait for the browser to launch)
- If you are using a different browser, or OpenRefine does not automatically open for you, point your browser at [http://127.0.0.1:3333/](http://127.0.0.1:3333/) or `http://localhost:3333` to launch the program.

**Windows Troubleshooting**

You may also need to install Java for Windows
- Check if your Windows is 32-bit or 64-bit help via: [https://support.microsoft.com/en-au/help/15056/windows-32-64-bit-faq](https://support.microsoft.com/en-au/help/15056/windows-32-64-bit-faq).
- Select appropriate bit download
  - 32-bit via: [https://www.java.com/en/download/](https://www.java.com/en/download/) or
  - 64-bit via: [https://www.java.com/en/download/manual.jsp](https://www.java.com/en/download/manual.jsp) and 
    select Windows Offline (64-bit) version
- Choose the folder location. Save the file to `c:\program files\`
- Close all applications including the browser.
- Double-click on the saved file icon to start the installation process.
  [https://www.howtogeek.com/129178/why-does-64-bit-windows-need-a-separate-program-files-x86-folder/](https://www.howtogeek.com/129178/why-does-64-bit-windows-need-a-separate-program-files-x86-folder/){% endcapture %}
{% include card.md header="Windows" text=text %}
  
{% capture text %}
- Check that you have Firefox or Chrome browsers installed and set as your default browser. OpenRefine runs in your default browser. It will not run correctly in Internet Explorer.
- Download latest software version from [http://openrefine.org](http://openrefine.org)
- Drag icon into `Applications folder`
- Doubleclick to launch OpenRefine
- If you are using a different browser, or OpenRefine does not automatically open for you, point your browser at [http://127.0.0.1:3333/](http://127.0.0.1:3333/) or `http://localhost:3333` to launch the program.
  
 **Mac Troubleshooting**
- If OpenRefine doesn’t open due to security settings go to:
  - `System Preferences> security & privacy >` see message re: OpenRefine
  - select Open anyway{% endcapture %}
{% include card.md header="Mac" text=text %}

{% capture text %}
- Check that you have Firefox or Chrome browsers installed and set as your default browser. OpenRefine runs in your default browser. It will not run correctly in Internet Explorer.
- Download the latest software version from [http://openrefine.org](http://openrefine.org). 
- Unzip the downloaded file into a directory. Name that directory something like OpenRefine.
- Go to your newly created OpenRefine directory.
- Launch OpenRefine
-Type `./refine` into the terminal within the OpenRefine directory
- If you are using a different browser, or OpenRefine does not automatically open for you, point your browser at [http://127.0.0.1:3333/](http://127.0.0.1:3333/) or `http://localhost:3333` to launch the program.{% endcapture %}
{% include card.md header="Linux" text=text %}

-----

## Download the data

Download the `QLDtrafficAccidentsOpenDataVer1.csv` dataset from this [website](https://research-storage.griffith.edu.au/owncloud/index.php/s/NphyCS2OvSIZe8E)
to your `Downloads` folder. We will then import that data into OpenRefine.

Alternately, when you launch OpenRefine, you can import the data directly from a Web address using this link [https://raw.githubusercontent.com/stapletonsl/ClassData2020/master/QLDtrafficAccidentsOpenDataVer1.csv](https://raw.githubusercontent.com/stapletonsl/ClassData2020/master/QLDtrafficAccidentsOpenDataVer1.csv)

-----


## Get help

##### Online

You can find out more at the [OpenRefine](http://openrefine.org) website.  Check out the [documentation](http://openrefine.org/documentation.html) and great introductory videos. These videos and others on OpenRefine can also be found on YouTube - use the search term 'OpenRefine'.

There is a [Google Group](https://groups.google.com/forum/#!forum/openrefine) that can answer a lot of beginner questions and problems.

##### At Griffith University

Help is available at Griffith [Hacky Hour & Library Researcher Support](https://hackyhourgriffith.wordpress.com/) sessions, Thursdays between 2-3pm alternating weeks at Gold Coast and Nathan campuses.  Grab a free coffee and we can help you.
Or get in touch with us [here](https://intranet.secure.griffith.edu.au/library/forms/help) for an online consultation.
