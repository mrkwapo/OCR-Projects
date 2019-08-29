This program was created 8/28/2019  to iterate within a folder of images and extract text from each image and create an of Instagram users.

8/29/2019 Because the inaccuracy of the OCR technology I will have to either use a different set of images to demonstrate or use different ORC technology with better accuracy. 

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

*$ npm init*

*(It will ask you to populate information about the project which will be stored in the package.json file. You can hit enter until it goes away and you can edit or add information later)

**Step 2** Install okrabyte

*$ npm install --save-dev okrabyte*

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

*$ node filename.js*

In the terminal, your results should show up in an array.

        Example:
        [ 'photo0.png',
          'photo1.png',
          'photo2.png',
          'photo3.png',
          'photo4.png',
          'photo5.png',
          'photo6.png',
          'photo7.png',
          'photo8.png',
          'photo9.png' ]


**Step 6**
Next we are going to wrap the code into an async function called "words()".

(async () => {
  **async function words() {**
    const files = await new Promise((resolve, reject) => {
      fs.readdir('images/', (err, files) => {
        if (err) {
          reject(err);
        } else {
          resolve(files);
        }
      });
    });
   );
   **}**
  })();

**Step 7**
Next we are going to iterate through all files using the map method and use a Promise to handle all the files after they have been resolved or rejected. And use okrabyte technology on each of the files. in fs.readFileSync method we are attaching "images/" to the front of each file name. Then we handle the error and results by rejecting the errors if any and then resolving the returned data. And outside of the promise we need to return the results *(return mapped)*.

const fs = require('fs');
const okrabyte = require('okrabyte');

(async () => {
  async function words() {
    const files = await new Promise((resolve, reject) => {
      fs.readdir('images/', (err, files) => {
        if (err) {
          reject(err);
        } else {
          resolve(files);
        }
      });
    });

    **const mapped = await Promise.all(
      files.map(file => {
        return new Promise((resolve, reject) => {
          okrabyte.decodeBuffer(
            fs.readFileSync('images/' + file),
            (err, data) => {
              if (err) {
                return reject(err);
              } else {
                resolve(data);
              }
            }
          );
        });
      })
    );
    return mapped;**
  }

})();

**Step 8**
In order to console log the results we need to await for the words() and then store it in a variable in which we will name "testing".

        });
      })
    );
    return mapped;
  }
 ** const testing = await words();

  console.log(testing);**
})();

**Step 9** Test the console log

*$ node filename.js*

It will take a while for the promise to return the results. And when the results return, they will be a mess but notice all the data is delivered in an array. You can use the .split() method to extract specific text from the results.


