# whatsapp_msg_analysis
Notebook to get statistics on Whats' App conversation. The program also generates automatically a PDF that sums up the results.

# How to get What's App conversation
## With Whats' App:
On your mobile phone, go on the conversation, click on the options (three dots on the top right of the windows), go to "more", and then click on "export chat" and send the conversation to your e-mail. You should receive a .txt. This .txt contains your conversation. You can convert it on the format used by my code by using "convert_txt_to_csv.ipynb" (see below). There are two limitations with this method: it only allows you to get 40'000 messages and the pattern used by Whats' App depends on the language you are using (thus, my conversion notebook may not work).

To convert to .txt to .csv, open the notebook "convert_txt_to_csv.ipynb", change FOLDER_NAME with the name (or path) of the folder that contains the file and change FILE_NAME with the name of the .txt file. Then run the whole notebook. The code will ask you to select between two patterns of messages, select the correct one and wait a bit before the code create data.csv, which is the conversion of your file towards my data frame format. If your pattern does not appear, that means that your WhatsApp is working in a different configuration than what I faced, but it should not be complex to adapt the code.

## With Chrome Extension
The Chrome extension "Backup WhatsApp Chats" returns the maximum of the conversation that it can (I was able to get 700'000 messages), returns it always with the same structure and in more exciting formats (CSV, HTML, ...). To use it, go to the chrome extension store, download it, pay for the license, open WebWhatsApp on a tab and select the conversation you want to export, open the extension, select CSV and the start and stop date, launch the code, after some time you will download the .csv file. **I do not know the people behind the Chrome Extension, and thus they may steal your data or whatever. If your data is sensitive, use the other method (or if you do not want to pay some dollars).**

# How to launch the analysis
## Prepare a list of stop words (optional)
If you did not download the .pkl, you could create them by running "create_stop_words.ipynb". The notebook will create the .pkl containing the list of stopwords for french and English. If you need another language, you can adapt the code to create your own .pkl.

## Select the parameters
On the top of the "whatsapp_discussion_stats.ipynb" you will find some parameters that you have to set. 
### File selection
First, set the path towards your file in FOLDER_NAME and the name of your file in FILE_NAME. Your file needs to respect my data frame structure defined at the top of the document. If you downloaded the .csv from the Chrome extension mentioned before or created the .csv using "convert_txt_to_csv.ipynb", the data frame should already have the correct format.
### Define a discussion
Second, select how do you want to define a live discussion. To do so, you can select the minimum number of messages that have been exchanged (NB_MSG_TH) and the maximum time between each message (RESPONSE_TIME_TH) in minutes. If no discussion can be found in the whole conversation, the code won't display statistics, but it will still run.
### Define the language
Third, select the language by changing *language*, default is "English" or "French", others will automatically try to download a list of stop words. If it fails, the code will still run but without stopwords.
### PDF genereation
Fourth, you can disable or enable the PDF generation by modifying *PDF*. You can also select where and which name to save the PDF in PDF_NAME.
## Check the libraries (optional)
You may install the libraries that you do not have. Note that some of them are optional.
## Launch the code
You can execute the whole notebook. Depending on the size of your conversation, the code may last more or less. For a conversation of 718'899 messages and 4'618'207 words, the program takes (without PDF generation) 3m30s on my computer (Lenovo ThinkPad P50).
## See the results
Some cells will display text with statistics and other plots. If you enabled PDF generation, you would find it at the specified location. Note that the code should also work for Whats' App group.

# Disclaimer and license
This project was developed as a hobby in some days. Thus it is not optimised nor completely clean; watch out before considering using it in a sensible application. For non-profit usage, do not hesitate to use it, else contact me at ivan.daniel.sievering@gmail.com. Feel free to contact me in case of bugs or enhancement to propose (but keep in mind that was just a hobby project).
