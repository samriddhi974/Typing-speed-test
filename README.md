# Typing-speed-test
# importing all libraries
from tkinter import *
from timeit import default_timer as timer
import random

# creating window using gui
window = Tk()

# the size of the window is defined
window.geometry("450x200")

x = 0

# defining the function for the test
def game():
	global x

	# loop for destroying the window
	# after on test
	if x == 0:
		window.destroy()
		x = x+1

	# defining function for results of test
	def check_result():
		if entry.get() == words[word]:

			# here start time is when the window
			# is opened and end time is when
			# window is destroyed
			end = timer()

			# we deduct the start time from end
			# time and calculate results using
			# timeit function
			print(end-start)
		else:
			print("Wrong Input")

	words = ['When I have built up my savings, I will travel to Goa.', 'Would not it be lovely to enjoy a week soaking up the culture?', 'The plots failed because of some trusted friends of the king.',
			'After the death of the king, everyone wanted to be a king.', 'War does not bring anything good to the common people.', 'If opportunity does not knock, build a door.']

	# Give random words for testing the speed of user
	word = random.randint(0, (len(words)-1))

	# start timer using timeit function
	start = timer()
	windows = Tk()
	windows.geometry("650x200")

	# use lable method of tkinter for labling in window
	x2 = Label(windows, text=words[word], font="times 17")

	# place of labling in window
	x2.place(x=100, y=10)
	x3 = Label(windows, text="Start Typing", font="times 16")
	x3.place(x=10, y=50)

	entry = Entry(windows)
	entry.place(x=250, y=60)

	# buttons to submit output and check results
	b2 = Button(windows, text="Done",
				command=check_result, width=12, bg='grey')
	b2.place(x=190, y=150)

	b3 = Button(windows, text="Try Again",
				command=game, width=12, bg='grey')
	b3.place(x=290, y=150)
	windows.mainloop()


x1 = Label(window, text="Lets start playing..", font="times 20")
x1.place(x=120, y=40)

b1 = Button(window, text="Go", command=game, width=12, bg='grey')
b1.place(x=180, y=135)

# calling window
window.mainloop()
