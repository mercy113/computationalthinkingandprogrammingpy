# Store the meetings
meetings = [
    ("M1", 9, 10),
    ("M2", 9, 12),
    ("M3", 10, 11),
    ("M4", 11, 13),
    ("M5", 12, 14),
    ("M6", 13, 15)
]

# Sort meetings according to finish time
meetings.sort(key=lambda x: x[2])

# Store selected meetings
selected = []

# Store the finish time of the last selected meeting
last_finish = -1

# Select non-overlapping meetings
for name, start, finish in meetings:

    # Check whether the meeting does not overlap
    if start >= last_finish:

        # Select the meeting
        selected.append((name, start, finish))

        # Update the last finish time
        last_finish = finish

# Display selected meetings
print("Selected Meetings:")

for name, start, finish in selected:
    print(name, ":", start, "to", finish)

# Display maximum number of meetings
print("Maximum Number of Non-Overlapping Meetings:", len(selected))

# OUTPUT
Selected Meetings:
M1 : 9 to 10
M3 : 10 to 11
M4 : 11 to 13
M6 : 13 to 15
Maximum Number of Non-Overlapping Meetings: 4
