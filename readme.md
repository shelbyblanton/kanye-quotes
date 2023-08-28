# Kanye West Quotes Application

## **[100 Days of Code: The Complete Python Pro Bootcamp for 2023](https://www.udemy.com/course/100-days-of-code/)**

By Dr. Angela Yu

*Day 33 of 100:* API Endpoints and Parameters

## Project Specs

Using **[TkInter](https://docs.python.org/3/library/tkinter.html)** and the **[Requests](https://pypi.org/project/requests/)** libraries, program an application where a user learns about life by reading quotes from **[Kanye West](https://en.wikipedia.org/wiki/Kanye_West)**.

This application is written with Python 3.11.

![US States Game Preview](https://github-readme.s3.us-west-1.amazonaws.com/KanyeWestQuotes.png)

### Main Features
To use the application, a user is presented with a speech bubble and Kanye West's face.

As the user clicks on Kanye's face, a new quote is entered into the speech bubble.

## Usage & Requirements

This project uses two libraries:
- TkInter
- Requests

### Workflow
We start by creating the Graphic User Interface (GUI) creating a new `Tk` class. Then using TkInter Canvas functionality, we populate the screen with our background graphics and our initial screen text:     

```angular2html
window = Tk()
window.title("Kanye Says...")
window.config(padx=50, pady=50)

canvas = Canvas(width=300, height=414)
background_img = PhotoImage(file="background.png")
canvas.create_image(150, 207, image=background_img)
quote_text = canvas.create_text(
    150,
    207,
    text="Click on Kanye below, and he will give you a famous quote of his!",
    width=250,
    font=("Arial", 30, "bold"),
    fill="white"
)
canvas.grid(row=0, column=0)
```

Then we add Kanye's face and tie the action of clicking on his head to acquiring the next quote by adding the `get_quote()` function as the button command:
```
kanye_img = PhotoImage(file="kanye.png")
kanye_button = Button(image=kanye_img, highlightthickness=0, command=get_quote)
kanye_button.grid(row=1, column=0)
```

Kanye's quotes are pulled from the `kanye.rest` API via the `get_quote()` function, using the Python **[Requests](https://pypi.org/project/requests/)** library package:

```
def get_quote():
    response = requests.get(url="https://api.kanye.rest/")
    response.raise_for_status()
    data = response.json()
    canvas.itemconfig(quote_text, text=data['quote'])
```

# Getting Started

All of the commands below should be typed into the Python terminal of your IDE (I use PyCharm for my Python Development).

First, clone the repository from Github and switch to the new directory:

    $ git clone git@github.com:shelbyblanton/kanye-quotes.git
    
Then open the project in PyCharm.
    
Open the Python Console and type the following to install the Python `Requests` package:

    >>> pip install requests

**Setup is complete!** 

Click Run in PyCharm to see the app in action.

# Author & Credits

Programmed by **[M. Shelby Blanton](https://www.linkedin.com/in/shelbyblanton/)** under the instructional guidance of **[Dr. Angela Yu](https://www.udemy.com/user/4b4368a3-b5c8-4529-aa65-2056ec31f37e/)** via **[Udemy.com](udemy.com)**.
