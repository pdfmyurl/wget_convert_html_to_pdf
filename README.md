
# Convert HTML to PDF with Wget on the Linux command line

The examples below use our [HTML to PDF API](https://pdfmyurl.com/html-to-pdf-api) to create PDFs from HTML or URLs. Many more options can be used to influence the layout of the PDFs as well as the way the conversion takes place.


## Wget URL to PDF conversion example

Here we're converting the example URL https://www.example.com to PDF and storing it in a file called "result.pdf".

    wget -O result.pdf --post-data="license=yourlicensekey&url=https://www.example.com" https://pdfmyurl.com/api

You can add additional parameters by adding them to the --post-data parameter. Make sure you URL encode all the parameters, so it would be better to use the following command instead for our example.

    wget -O result.pdf --post-data="license=yourlicensekey&url=https%3A%2F%2Fwww.example.com" https://pdfmyurl.com/api

## Wget HTML to PDF conversion example

This example will convert raw HTML to a PDF with the name "result.pdf". Since you want to usually convert quite a bit of HTML to get a full PDF, it makes sense to store the HTML in a file first before using Wget. Otherwise your Wget command becomes really large, just due to the html parameter.

Since Wget doesn't have the option to use multiple parameters separately, it's better to use the --post-file parameter. In that case you need to store all the parameters in a file, in the same way that you would normally pass them to --post-data. 

So your file would contain the parameters in URL encoded format, like this:

    license=yourlicensekey&html=%3Cb%3EHello%3C%2Fb%3E

The above example file contains two parameters:

 1. license with the value *yourlicensekey* (replace this with your own license key)
 2. html with the URL encoded value for `<b>Hello</b>`

When you create a file like this and store it as "data.txt" you can then use Wget to use it and convert the HTML to PDF with the following command.

    wget -O result.pdf --post-file="data.txt" https://pdfmyurl.com/api

To use this example just copy/paste it and make sure you have a file named "data.txt" in the current directory that contains the parameters as above.
