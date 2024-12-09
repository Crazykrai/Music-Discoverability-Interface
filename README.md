# Horizon

For Project 4 I elected to create an interface to address and help improve music discoverability. Music is in my opinion one of the cornerstones of our culture as a whole,
so that led me to place enough importance on being able to easily discover new music. Improved discoverability would also be a major help to up-and-coming artists who may
struggle to get the same reach that bigger artists get on current music and streaming platforms. Creating a way to give people more opportunities to discover new music would 
only serve as a way to further enrich their lives.

A user interface to address this problem would need to deviate from the norm already established by current major music services such as Spotify. Having different interfaces
to give users more options will lead to more opportunities to discover new things based on the different implementations of each interface. One such idea for my interface
is to display a completely random song and artist of the day. This approach helps break through the curated selections built up by algorithms in other streaming services
to give users a chance to discover something completely brand new.

---

## Design Work and Sketches
insert sketch photos

### Research

To collect information about this problem, I interviewed a few friends of mine who listen to music very often. One big problem stated about finding new music 
was that there are genres a person could like that they wouldn't know until they had actually tried it. Current systems such as Spotify recommend songs based on your 
listening history which can discourage branching out from your current music. Another big problem was how indie artists would never be able to get a chance due to being covered up
by larger artists.

## Interface Controls and Features

![alt text](<images/image (2).png>)
- **Home Page**
    - Landing page of the website with an info section for any commonly asked questions

![alt text](<images/image (3).png>)
- **Filters**
    - Users can use this to filter the random song and artist they get shown to give a greater chance of relevant results they would like

![alt text](<images/image (4).png>)
- **Song Chart**
    - Gives users insight into current song metrics of the day, allowing them to see the most popular, trending, and indie/underground songs

![alt text](<images/image (5).png>)
- **Song of the Day**
    - Main section of the song and artist page that displays today's random selection based on the user's filters. Save button allows the user to add it to the 'saved' page

![alt text](<images/image (6).png>)
- **Saved Items**
    - Allows users to view any previously saved song or artist, as well as remove any currently saved selections

## Code Implementation
For this project, I utilized a component library called ShadCN alongside TailwindCSS to create the overall structure of each page as well as the major elements. The random song and artist is displayed by using Spotify's embed iframe API. The interface despite navigating to different sections is still technically all done in a single page, with the buttons just controlling which parts of the component are displayed to the user. 

## Use of AI
No AI was used to assist in the development of this project.

## Future Work
With more time, I would like to continue adding more customization features, such as more filtering options and the ability to edit the order of your saved items. I would also turn it into a full-stack application to actually connect to databases to pick out a fully random song instead of having built-in ones for demonstration purposes. 

--- 

## Demo & Links

- **Demo Video:** [Watch the Demo](https://drive.google.com/file/d/1yfSp0yOhstkcl4n_a1kDpavizRaGH6Qg/view?usp=sharing)
- **Public Link:** [steam-library-redesign.vercel.app](https://music-discoverability-interface.vercel.app/)