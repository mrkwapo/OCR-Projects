This program will iterate within a folder of images and extract text from each image and create an of Instagram users.


**STEPS TO CLONE**

**Step 1: Initiate Git** in the terminal, type and enter:

$ git init

**Step 2: Clone repository** in the terminal, type and enter:

git clone https://github.com/mrkwapo/OCR-Projects.git

**Step 3: Initiate NPM in terminal**

$ npm init



**Step 4: Install dependencies** in the terminal, type and enter:

$ npm install


**TECHNOLOGIES USED:**

*INSTALL:*
**Okrabyte** is a javascript Optical Character Recognition(OCR) library for with Node.js. It scans images for text characters. 
*See documentation:* https://www.npmjs.com/package/okrabyte .

**Visual Studio Code** provides a code editor and terminal. 
*See documentation and download:* https://code.visualstudio.com/download

**Node.js** is an open-source, cross-platform, JavaScript run-time environment that executes JavaScript code outside of a browser.
  *See documentation and download:* https://nodejs.org/en/ 
  
  
  *GLOSSARY:*
  
  fs : The Node.js **f**ile **s**ystem module allows you to work with the file system on your computer.
            Common use for the File System module:
                  Read files
                  Create files
                  Update files
                  Delete files
                  Rename files

            To include the File System module, use the require() method:
              Example: 
                  var fs = require('fs');

**STEP BY STEP TUTORIAL**

Inside the root directory, create a folder and name it "images". Save 10 screenshots of instagram user profile pages and store them inside the folder named "images". (To avoid complications, avoid using profiles with words in their profile photos.)


**Step 1** Initiate Node Package Manager (NPM)

*$ npm init

*(It will ask you to populate information about the project which will be stored in the package.json file. You can hit enter until it goes away and you can edit or add information later)

**Step 2** Install okrabyte

*$ npm install --save-dev okrabyte

**Step 3** Create a js file in the root directory (not inside the images folder) and type the following:

const fs = require("fs");  
const okrabyte = require("okrabyte");



**Step 4**
After bringing in fs and okrabyte, we will need to use an asynchronous function. Because the action *readdir (which means read directory)* takes time to respond instead of immediately we will be using async/await functions to handle promises which will return our results. The first argument tells the readdir function where to look for the files. We will use a callback function (err, files) as a second argument to throw an error or return files in the directory designated in arguement one. If there is an error it will reject any errors. Otherwise, we will resolve the files. *To learn about asynchronous functions, promises and callbacks, see:  https://javascript.info/async*

const fs = require("fs");  
const okrabyte = require("okrabyte");

**(async() => {
  const files = await new Promise((resolve, reject) => {
    fs.readdir('images/', (err, files) => {
      if(err){
        reject(err);
      }else {
        resolve(files);
      }
    });
  });
  console.log(files);

**})()** 

(this is the set up of an E6 self executing arrow function. See here for more information: )

**Step 5**
To check the results stored in the variable "files", we console log, then run the program in the terminal with the following command:

*$ node filename.js

Your results should show up in an array.

        Example:
        [ 'photo1.png',
          'photo10.png',
          'photo2.png',
          'photo3.png',
          'photo4.png',
          'photo5.png',
          'photo6.png',
          'photo7.png',
          'photo8.png',
          'photo9.png' ]


**Step 6**

**Step 7**
