<!-- TITLE: Python Files -->
<!-- SUBTITLE: A quick summary of Python Files -->

# Open with mode
f = open("demofile.txt", "rt")

# Read entire file
f = open("demofile.txt", "r")
print(f.read()) 

# Read 5 bytes
print(f.read(5))

# Read a line
print(f.readline()) 

# Loop through by line
f = open("demofile.txt", "r")
for x in f:
  print(x) 
	