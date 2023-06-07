![](http://ForTheBadge.com/images/badges/made-with-python.svg)
![](https://forthebadge.com/images/badges/built-by-developers.svg)</br>
![Size](https://img.shields.io/github/repo-size/Iamtripathisatyam/Mini_Assistant?color=red&label=Repo%20Size%20)
[![Prettier](https://img.shields.io/badge/Code%20Style-Prettier-red.svg)](https://github.com/prettier/prettier)
![](https://img.shields.io/tokei/lines/github/Iamtripathisatyam/Mini_Assistant?color=red&label=Lines%20of%20Code)
![License](https://img.shields.io/badge/License-MIT-red.svg)</br>
![](https://profile-counter.glitch.me/{Mini_Assistant}/count.svg)

<p align="center">
<a href="https://github.com/Iamtripathisatyam/Mini_Assistant/blob/main/Content/code.py"><img width="20%" src="https://user-images.githubusercontent.com/69134468/128800245-60875112-29c5-4801-8023-e9d84a834b24.png" /></a>
</p>

- [Introduction](#Intro)
- [What can Assistant do?](#do)
  - [Wish you (Good Morning, Good Afternoon, and Good Evening) according to time](#wish) 
  - [Search on Wikipedia](#wiki)
  - [Search on YouTube](#you)
  - [Search on Google](#goog)
  - [Send Email](#mail)
  - [Keep Notes](#notes)
  - [Time](#time)
  - [Date](#date)
  - [Play Music](#music)
  - [Send Notifications](#noti)
  - [Maths Calculations](#maths)
  - [Words Meaning](#words)
  - [Weather Notifications](#weath)
  - [Battery of your PC](#batt)
  - [ShutDown your PC](#shut)
  - [Search Locations](#locate)
  - [Download Video](#download)
  - [Tell Jokes](#joke)
  - [reSTART](#restart)
  - [Take a Photo](#photo)
  - [Empty Recycle Bin](#bin)
- [Output](#out)
- [Conclusion](#conc)
- FAQ (Frequently Asked Questions)

## Introduction:<a name="Intro"></a>
This project helps you do many things on the internet. You can send emails, search on YouTube and Google, find places, enjoy jokes, get phone alerts, and more.

When you start the project, it shows a nice screen with options and a next button. Then, you'll see a box where you can type what you want, like searching on Google or Wikipedia.

If you type something wrong or that **doesn't exist**, it shows an error message, and you **can't continue**. It also shows messages when things work well, warnings, and important info in small windows.

## What can Assistant do?<a name="do"></a>
- ### Wish you: <a name="wish"></a>
  - It can greet you based on the time using a special module called **"datetime".**

Here's how it works:

	- The code calculates the current hour using "datetime.datetime.now().hour".
	- Then, it uses if-else loops to figure out the best greeting for that time.
	- If the hour is between 5 AM and 12 PM, it says "Good Morning".
	- If the hour is between 12 PM and 5 PM, it says "Good Afternoon".
	- Otherwise, it says "Good Evening".

  - Using the below code, it will first calculate an hour.
    
    ```python
    hour = int(datetime.datetime.now().hour)
    ```
  - Following that, it will use some if-and-else loops to determine the ideal timing for the wishes.
    
    ```python
    if hour >= 5 and hour < 12:
        print("Good Morning")
    elif hour >= 12 and hour < 17:
        print('Good Afternoon')
    else:
        print('Good Evening')

    ```
- ### Search on Wikipedia:<a name="wiki"></a>
  - Here's how it works:

	- First, it asks the user to enter something they want to search for on Wikipedia.
	- Using the Wikipedia module, it checks if the input exists on Wikipedia.
	- If it does, it tries to get a summary of the topic using relevant keywords.
	- If the input is not found on Wikipedia, it suggests some alternative keywords to search for.

    ```python
    Test_string = input(placeholder="Wikipedia Search", required=True)
    ```
  - It will initially seek input from the user. It will now check to see whether if the input exists in Wikipedia. If it's in Wikipedia, we'll try to get a summary by providing some relevant keywords.
    
    ```python
      Result = wikipedia.summary(Test_string, sentences=2, auto_suggest=False, redirect=True)
    ```
  - If it isn't found on Wikipedia, the suggested keywords will be searched using the approach described below.
    
    ```python
    Test_string = wikipedia.suggest(Test_string)
    ```
    
    
- ### Search on YouTube: <a name="you"></a>
  - Here's how it works:
	- First, it asks the user to enter something they want to search for on YouTube.
	- With the help of a special module called "Webbrowser," it performs the search operation.
	- It opens a web browser window and shows the search results on YouTube.

    ```python
    Test_string = input(placeholder="YouTube Search", required=True)
    ```
  - For searching on YouTube, it will now use the ***open*** function specified in the webbrowser module.
   
    ```python
    webbrowser.open(f"https://www.youtube.com/results?search_query={Test_string}")
    ```
    
    
- ### Search on Google:<a name="goog"></a>
  - Here's how it works:

	- First, it asks the user to enter something they want to search for on Google.
	- With the help of a special module called "Webbrowser," it performs the search operation.
	- It opens a web browser window and shows the search results on Google.

    ```python
    Test_string = input(placeholder="YouTube Search", required=True)
    ```
  - For searching on Google, it will now use the ***open*** function specified in the webbrowser module.

    ```python
    webbrowser.open(f"https://www.youtube.com/results?search_query={Test_string}") 
    ```
- ### Send Emails:<a name="mail"></a>
  - **Register User Email ID:** To allow yagmail to access our Gmail account and send emails, we register our Gmail username and password. 
  
    ```python
    yagmail.register("Sender’s Gmail Username", "Sender’s Gmail Password")
    ```
  - **Connect to SMTP server:** To initiate a connection with the SMTP server using the SMTP client, use the command below.
    
    ```python
    yag = yagmail.SMTP(“Sender@gmail.com”)
    ```
  - **Adding Content and Delivering:** 
     - In 1st argument in send() function, pass the receiver’s email address.
     - Then in the 2nd one, pass the Subject of the Mail your sender is sending.
     - Now in the 3rd one, pass the  Content of Mail i.e text or media.
     </br>
     
     ```python
      yag.send(“Reciever@gmail.com”,”Subject Of Mail”,”Content(Text, Media etc)”)
      ```
   
- ### Keep Notes: <a name="notes"></a>
    - To create a new note:
		- Provide a title and the contents for the note.
		- The assistant uses a special library called SQLAlchemy, which stores and 		     tracks the notes using a database called SQLite.


    - **Creating the database:**</br>

	    ```python
	    engine = db.create_engine('sqlite:///notes.db')
	    metadata = db.MetaData()
	    notes = db.Table('notes', metadata, db.Column('Time', db.String(255), nullable=False, primary_key=True), db.Column(
		 'Title', db.Text(), nullable=False, primary_key=True), db.Column('Note', db.Text(), default=''))
	    metadata.create_all(engine)
	    ```
    - **Enterting a note:** 
		- When entering a note, this function is called.
		- The new note is saved in the database with the provided title and contents.
    
	    ```python
	    def enterNote(title,note):
	    current_dateTime = str(datetime.now())
	    try:   
		connection = engine.connect()     
		query = db.insert(notes).values(Time=current_dateTime,Title=title,Note=note)
		result = connection.execute(query)
		connection.close()
	    except Exception as e:
		print(e)
	    ```
    - **Viewing a note:** 
	    - When viewing a note, this function is called.
	    - The note with the specified title is retrieved from the database and displayed.<br>
    
	    ```python
	    def displayNote(title):
	    try:
		connection = engine.connect()
		s = notes.select().where(notes.columns.Title==title)
		result = connection.execute(s)
		for row in result:
		    print(row[2])
		connection.close()

	    except Exception as e:
		print(e)
	    ```
        
- ### Time: <a name="time"></a>
		- We use the datetime module and a specific command to get the current time.
		- The code provides the time in a specific format: hour, minute, and AM/PM.
      
      ```python
      datetime.datetime.today().strftime("%I:%M %p")
      ```
- ### Date: <a name="date"></a>
  - To find the current date, we'll use the ***datetime*** module.
  - Now, we will simply use ***%m*** to get the month number, and then we will use ***%b*** to get the month name. 
  </br>
  
     ```python
    current_time = datetime.datetime.now()
    datetime_object = datetime.datetime.strptime(str(current_time.month), "%m")
    month_name = datetime_object.strftime("%b")
     ```
 - ### Play music: <a name="music"></a>
 		 - Enter the name of the song or music without spaces.
		- The assistant will quickly play the exact song or music.
		- It uses two libraries: "Pytube" to access the songs/music and "Playsound" to play them.
    
- Generating the URL of the Song:
	- To generate the song URL from the song name:
		- The code takes the song name and searches for it on YouTube.
		- It retrieves the video ID from the search results to create the URL.
	    ```python
	    def generateURL(songName):	
		    search_keyword= str(songName)
		    html = urllib.request.urlopen("https://www.youtube.com/results?search_query=" + search_keyword)
		    video_ids = re.findall(r"watch\?v=(\S{11})", html.read().decode())
		url = "https://www.youtube.com/watch?v=" + video_ids[0]
	    ```
    - After the generation of the song URL, we can play the song using it: </br>
    	- To play the song:
			- The generated URL is used to access the song on YouTube.
			- The audio stream of the song is extracted and saved as an MP3 file.
			- Finally, the song is played using the "Playsound" library.

	    ```python
	    def playSong(url):
	      yt = YouTube(str(url))
	      audio = yt.streams.filter(only_audio=True).first()
	      out_file = audio.download()
	      base, ext = os.path.splitext(out_file)
	      new_file = base + '.mp3'
	      os.rename(out_file, new_file)
	      playsound(new_file)
	    ```
    
 - ### Send Notification:<a name="noti"></a>
	- Visit Pushbullet and acquire the access token.
	- Retrieve your Access Token and utilize the PushBullet method to create an instance by providing the Access Token in the PushBullet function. 

  
      ```python
      PushBullet(access_token)
      ```
   - Utilize the push_note function to send data and text. This function requires two arguments: data and text. The first argument serves as a heading in the notification, while the second argument represents the main text content.
   
       ```python
       pb.push_note(data, text)
       ```
- ### Maths Calculations: <a name="maths"></a>
    	-The assistant can help with various types of mathematical calculations. It can act as a verbal calculator, providing answers through spoken 	     	responses. It supports the following operations:
	
	- Arithmetic operations: Addition, subtraction, multiplication, division, and finding the square root.
	Trigonometric operations: Sine, cosine, and tangent.

	    **Examples**:
	    ```
	    command: Hey jarvis, add 5 and 5
	    output : 10

	    command: Hey jarvis, find the product of 6 and 5
	    output : 30

	    command: Hey jarvis, find the square root of 169
	    output : 13

	    command: Hey jarvis, find the sin of 90 degrees
	    output : 1.0
	    ```
- ### Words Meaning:<a name="words"></a>
  - Load the ***JSON*** data
    
    ```python
    json.load(open(r"C:\Users\Dell\Downloads\ebooks.json"))
    ```
  - To return the definition of the word(entered by user).
  - This function will give an appropriate message, if the word doesn't exist in the data.
  - If user will enter a word with wrong spelling, then we have to give an appropriate message using ***get_close_matches()*** function.

- ### Weather Notifications:<a name="weath"></a>
  - Firstly, get the ***API*** key from [**OpenWeather.org**](https://openweathermap.org/) to begin extracting data.
  - User need to create an account on [**OpenWeather.org**](https://openweathermap.org/), then only can use the APIs. 
    
    ```python
    api_key = "Your API Key"
    base_url = "https://api.openweathermap.org/data/2.5/weather?"
    ```
  - Take City name as input and check whether city name is valid or not, and ***required=True*** means field can't be empty.
  - Extract all the data including ***Temperature***, ***Pressure***, ***Humidity***, ***Weather***, and ***Description***.

- ### Battery:<a name="batt"></a>
  - The ***psutil*** function will be used to perform battery-related tasks.
  - First, using the method outlined below, collect all the necessary information about the battery's present state.
  
    ```python
    battery = psutil.sensors_battery() # sbattery(percent=93, secsleft=19845, power_plugged=False)
    ```
  - After that we will only extract the battery with the uwse of battery function.
    
    ```python
    percent = battery.percent
    ```
  - Check whether the plug is plugged in or not.
    
    ```python
    pluged = battery.power_plugged
    ```
- ### ShutDown:<a name="shut"></a>
  - Shutting down the PC is a straightforward process that can be done with the help of the OS module.
  - The code below will shut off your computer.
    
    ```python
    os.system("shutdown /s /t  1")
    ```
- ### reSTART:<a name="restart"></a>
  - reSTARTing down the PC is also a straightforward process that can be done with the help of the ***OS*** module.
  - The code below will shut off your computer.
    
    ```python
    os.system("shutdown /r /t  1")
    ```
- ### Search Locations:<a name="locate"></a>
  - With the help of the ***webbrowser*** module, we can simply search for any place.
  - If a place exists, the code below will look for it.
    
    ```python
    webbrowser.open_new_tab("https://www.google.com/maps/place/"+what)
    ```
    
- ### Download video: <a name="download"></a>
   - You can download any Youtube video with its URL.
   - Just enter the URL of the Youtube video and the video gets downloaded.
   - It will be saved in the default **Downloads** folder in your System
   - A library called **Pytube** is used to download the video.

	  ```python
	  def downloadYTVideo(url):
	    try:
		youtube = pytube.YouTube(url)
		video = youtube.streams.filter(progressive=True,file_extension='mp4').desc().first()
		path = str(os.path.join(Path.home(),'Downloads')
		video.download(output_path=path)
	    except Exception as e:
		print(e)
	   ```

- ### Jokes:<a name="joke"></a>
  - We will use the ***pyjokes*** module for this.
  - The ***get_joke*** function is defined in the pyjokes module: simply pass the *language*and *category* of the joke.
  
    ```python
    pyjokes.get_joke(language="en", category="neutral")
    ```
- ### Take a Photo:<a name="photo"></a>
  - The ***OpenCV*** module will be used to capture the images.
  - We will capture an image using the ***VideoCapture*** function specified in ***Opencv*** and read the pixels of the picture using the ***read*** function.
    
    ```python
    camera = cv2.VideoCapture(0)
    _, image = camera.read()
    ```
  - Finally, we'll write the image and save it with a name.
    
    ```python
    cv2.imwrite(name+".png", image)
    ```
    
 - ### Empty Recycle Bin:<a name="bin"></a>
    - We'll use the ***winshell*** module to empty the recycling bin.
    - The ***recycle bin ().empty*** function in the winshell module is empty the recycle bin.
    - The code below will help us in doing this.

      ```python
      winshell.recycle_bin().empty(confirm=False, show_progress=False, sound=False)
      ```
## Output: <a name="out"></a>
<p align="center"><img width="80%" src="https://user-images.githubusercontent.com/69134468/128981899-4cc19a45-1919-40bf-bcda-49d39c2c2b05.PNG"></p>

## Conclusion: <a name="conc"></a>
This is how easy it is to create your own desktop assistant. You may add many more functionalities, such as sending messages in Slack, providing data on Covid-19 cases, and so forth. Have fun experimenting with and creating your own Alexa/Siri/Cortana.

## FAQ (Frequently Asked Questions) 
Q: What is Marvin-Assistant?
A: Marvin-Assistant is an AI-powered chatbot designed to provide assistance and answer questions on a variety of topics.

Q: How do I install and run Marvin-Assistant?
A: To install and run Marvin-Assistant, you can follow the instructions provided in the project's documentation or README file on the GitHub repository.

Q: What programming language is Marvin-Assistant built with?
A: Marvin-Assistant is built using the Python programming language.

Q: Can I customize the responses and behavior of Marvin-Assistant?
A: Yes, you can customize the responses and behavior of Marvin-Assistant by modifying the code and configuration files according to your requirements.

Q: Can Marvin-Assistant understand multiple languages?
A: The language capabilities of Marvin-Assistant depend on its implementation. However, with appropriate configuration and language processing tools, it can be trained or adapted to understand and respond in multiple languages.

Q: Is Marvin-Assistant capable of learning and improving over time?
A: The learning and improvement capabilities of Marvin-Assistant depend on the specific implementation and training methods used. It is possible to incorporate machine learning techniques to enable learning and improvement over time.

Q: How secure is the data and information provided to Marvin-Assistant?
A: The security and privacy of the data and information provided to Marvin-Assistant depend on the implementation and the measures taken to ensure confidentiality and data protection. It's important to follow best practices for securing user data when developing and deploying a chatbot or assistant.

## Troubleshooting Questions/Answers for Dyselxia Students 
Q: I'm finding it difficult to read the responses from Marvin-Assistant. Is there a way to make the text more readable?
A: Absolutely! You can try adjusting the font size, color, or contrast settings of the interface where Marvin-Assistant is displayed. Increasing the font size, using a dyslexia-friendly font, or choosing high contrast options can often improve readability. Additionally, using text-to-speech or screen reader software might be helpful to have the responses read aloud to you.

Q: I frequently misspell words in my queries to Marvin-Assistant, and it affects the accuracy of the responses. How can I overcome this issue?
A: Dyslexia can make spelling challenging, but there are strategies to help. If possible, consider using a spell-checking tool or enabling auto-correction features on the device or application you are using to interact with Marvin-Assistant. You can also try using voice-to-text software or dictation tools to input your queries, which may help mitigate spelling errors. Remember, Marvin-Assistant's understanding may not be perfect, so providing clear and concise queries can also improve accuracy.

Q: I sometimes get overwhelmed by long or complex responses. Can I request Marvin-Assistant to provide shorter, simplified explanations?
A: Yes, you can definitely ask Marvin-Assistant to provide shorter or simplified explanations. You can phrase your request in a way that asks for concise answers or asks Marvin-Assistant to break down complex information into simpler terms. Feel free to specify your preferences for more accessible responses, and the assistant can adapt accordingly.

Q: I struggle with remembering information from previous interactions with Marvin-Assistant. Is there a way to review past conversations?
A: Absolutely! You can ask Marvin-Assistant if it has a history feature or if it can recap previous conversations. If the feature is available, you might be able to access a summary or transcript of your past interactions. This way, you can easily refresh your memory and refer back to any information you may have forgotten.

Q: I have difficulty with reading and comprehension. Can Marvin-Assistant provide information using alternative formats, such as audio or visual aids?
A: Depending on the capabilities of Marvin-Assistant, it may be possible for it to provide information using alternative formats. You can ask if it supports audio responses or if it can provide visual aids, such as images, diagrams, or videos, to enhance understanding. If these features are not available, consider using text-to-speech software or requesting assistance from someone who can convert the text-based information into a more accessible format for you.

___________________________________

<p>&copy; 2021 Satyam Tripathi</p>
