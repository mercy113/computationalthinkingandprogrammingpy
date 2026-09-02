# Greedy Algorithm

## 2. Meeting Room Scheduling

A company has one conference room that is shared by different teams.

Several meetings are scheduled during the day, and each meeting has a start time and finish time.

### Question

Explain how the Greedy Algorithm can be used to select the maximum number of non-overlapping meetings.

### Solution

According to the scenario, the Greedy Algorithm can be applied to the meeting room scheduling problem.

The main idea is to always select the meeting that finishes earliest.

By selecting the earliest finishing meeting, more time is available for the remaining meetings.

### Example

Imagine a company has one conference room and six meetings.

Meetings:

M1: Start Time = 9, Finish Time = 10

M2: Start Time = 9, Finish Time = 12

M3: Start Time = 10, Finish Time = 11

M4: Start Time = 11, Finish Time = 13

M5: Start Time = 12, Finish Time = 14

M6: Start Time = 13, Finish Time = 15

We want to select the maximum number of non-overlapping meetings.

### 1. Sort the Meetings

First, sort all meetings according to their finish time.

Sorted meetings:

M1 = 9–10

M3 = 10–11

M2 = 9–12

M4 = 11–13

M5 = 12–14

M6 = 13–15

### 2. Select the First Meeting

Select M1 (9–10) because it has the earliest finish time.

Last Finish Time = 10

### 3. Check M3

M3 starts at 10 and M1 finishes at 10.

Since 10 >= 10, select M3.

Selected Meetings: M1, M3

Last Finish Time = 11

### 4. Check M2

M2 starts at 9, but the previous meeting finishes at 11.

Since 9 < 11, M2 overlaps with the previous meeting.

Therefore, M2 is rejected.

### 5. Check M4

M4 starts at 11 and the previous meeting finishes at 11.

Since 11 >= 11, select M4.

Selected Meetings: M1, M3, M4

Last Finish Time = 13

### 6. Check M5

M5 starts at 12, but M4 finishes at 13.

Since 12 < 13, M5 overlaps with M4.

Therefore, M5 is rejected.

### 7. Check M6

M6 starts at 13 and M4 finishes at 13.

Since 13 >= 13, select M6.

Selected Meetings: M1, M3, M4, M6

### Final Result

The maximum number of non-overlapping meetings is 4.

Selected Meetings:

M1 → M3 → M4 → M6

# Algorithm

### Input

* List of meetings
* Start time of each meeting
* Finish time of each meeting

### Steps

1. Store all meetings with their start and finish times.
2. Sort the meetings according to their finish time.
3. Select the first meeting.
4. Store its finish time as the last finish time.
5. Check each remaining meeting.
6. If the start time of the current meeting is greater than or equal to the last finish time, select the meeting.
7. Update the last finish time.
8. Continue until all meetings are checked.
9. Display the selected meetings.
10. Count the selected meetings.

# Python Implementation

```python
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
```

# Output

```text
Selected Meetings:
M1 : 9 to 10
M3 : 10 to 11
M4 : 11 to 13
M6 : 13 to 15
Maximum Number of Non-Overlapping Meetings: 4
```

# Time Complexity

Sorting the meetings takes O(n log n) time.

Checking each meeting takes O(n) time.

Therefore, the overall time complexity is:

O(n log n)

Space Complexity:

O(n)

# Conclusion

The Meeting Room Scheduling problem can be solved efficiently using the Greedy Algorithm.

The algorithm always selects the meeting that finishes earliest.

For the given example, the selected meetings are:

M1 → M3 → M4 → M6

Therefore, the maximum number of non-overlapping meetings is 4.
