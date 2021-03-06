#  CheckIn--HackUMassV
David Medina, Declan Gray-Mullen, Eric Thompson-Martin, Jun Ru Anderson

## Inspiration
My grandfather, who lived alone, once fell in his kitchen. Because no one routinely checked in on him, he lay there for two and a half days before one of my aunts happened to call him and realize that something was wrong. This reflects the larger problem in America of elderly people (and especially elderly people suffering from degenerative brain disease) living alone and not receiving the frequent check ins that they need. When we heard about Optum's challenge to build something related to health, we were inspired to tackle this problem.

## What it does
On the elderly person's end, CheckIn runs continuously. It delivers reminders at specified times and receives verbal confirmation that the reminder was received. The audio user interface out of the terminal (as opposed to an app with a GUI) allows CheckIn to be used by people who couldn't use a mobile app or couldn't remember to log in to a website routinely.

A mobile app allows a Checker (who might be a caretaker, child or other contact of the elderly person) to set reminders for their elderly charge at a given time with a customized message. The format of the audio script expects reminders to be formatted as a question for which an affirmative answer means that the person is doing well. For example, for the question"Are you all right?" works correctly, while "Have you fallen down?" does not. This Checker will be notified via Facebook if their charge misses a CheckIn.

## How we built it
We wrote the audio user interface as a Python script that runs from the terminal. It uses Sphinx CMU voice recognition and Amazon Polly text-to-speech to communicate with the person receiving reminders. We wrote the mobile application using Swift. We used Dropbox to facilitate communication between the script and the app, and used Facebook's API to send messages to the Checker.

## Challenges we ran into
Our biggest challenge was deciding how the Python script and the mobile app would communicate. As a team, we lacked experience working with databases and servers. To circumvent this, we used a JSON file as a database and stored it in Dropbox, where both the Python script and the mobile app can download it, make changes, and re-upload it.

Another challenge we encountered was how to alert the Checker that the patient had missed their CheckIn. Both giving push notifications and sending text messages turned out to be more difficult than we expected. After researching the problem further, we determined that Facebook messenger was our best option giving the time constraints of this hackathon.

## Accomplishments that we're proud of
We're proud that it works. Though the current implementation doesn't scale particularly well, a person can receive daily reminders, and a Checker can add new reminders, modify existing ones, and will receive a Facebook message if CheckIn does not receive an affirmative response to the reminder.

## What we learned
We learned a number of skills. Half of us learned a new programming language this weekend, and all of us learned more about the various APIs we used. More broadly, we learned that when the initial solution to a problem is out of reach, there is almost always a workaround.

## What's next for CheckIn
There are two critical next steps. The first is improving scalability. Using a Dropbox folder in place of a server works while the database remains small, but downloading the entire database is both impractical and a security concern. The other next step is to make the audio script more flexible; allowing the expected response to be negative, for example, would allow CheckIn to work in a wider range of situations.
