#!/usr/bin/env python
# coding: utf-8

# # Instructions
# Enter the number of time blocks and partcipant names below. Newer NAMers first and long-timer NAMers last.

# In[22]:


NUM_BLOCKS = 4
NAMES = """
name 1
name 2
name 3
name 4
name 5
name 6
name 7
name 8
name 9
""".split('\n')[1:-1]

ROOM_URLS = [
    "meet.google.com/bng-zphm-ijz",
    "meet.google.com/exa-qwwg-ohh",
    "meet.google.com/btf-yfvd-nif",
    "meet.google.com/uir-zwqs-yrx",
    "meet.google.com/onb-vpxw-tzu",
    "meet.google.com/zie-tzbi-gfi",
    "meet.google.com/qhu-bhsx-gak",
]

num_rooms = int(len(NAMES) / 2)
assert len(ROOM_URLS) >= num_rooms, "Need at least {} rooms URLs but was only given {}.".format(num_rooms, len(ROOM_URLS))


# In[30]:


# Generate room assignments.
def compute_room(id, block):
    if id == 2 * num_rooms:
        # This person will be in groups of three. 
        return (id + (num_rooms - 1) * block) % num_rooms
    elif id < num_rooms:
        return id
    else:
        return (id + block) % num_rooms

# Format is: block_to_id_to_room[block][name_id] = room_id
block_to_id_to_room = [
    [compute_room(id, block) for id in range(len(NAMES))]
    for block in range(NUM_BLOCKS)
]


# In[36]:


# Print CSV.
columns = ["Name"]
columns += ["Block " + str(block) for block in range(NUM_BLOCKS)]
columns_tsv = '\t'.join(columns)
rows_tsv = ''
for name_id in range(len(NAMES)):
    rows_tsv += NAMES[name_id] + '\t'
    rows_tsv += '\t'.join([
        '=HYPERLINK("' + ROOM_URLS[block_to_id_to_room[block][name_id]] + '", "ROOM")'
        for block in range(NUM_BLOCKS)]) + '\n'
print(columns_tsv)
print(rows_tsv)
