## Twilio interview experience

Interviewing for big tech I always a very scary and ambitious situation. Recently I interviewed for a summer intern in [Twilio](https://twilio.com) and here's how it went down.

## A few pointers before we start:
- It was an on-campus opportunity  🏫
- Yes, I got selected 🎉
- The CTC for full-time was 43.4LPA (16LPA in hand) 💰
- My stipend is 1.22LPA (84k in hand) 💰

# Rounds

### 1. Coding round (90mins)
It was one of the best coding round I ever gave, for a change the problems weren't just random DSA problem but were actually based real world problem and were framed like a story in the terms of a problem faced by Twilio.

The first question was pretty simple, I don't exactly remember but it was something like


> Given an array of files, having to data points
> 1. file URL
> 2. file size in bytes
>
> We have to return files in categories of KB, MB, GB
> 
> input : [['link', 1234], ...]

The second question was a string manipulation question

> Given a string use some given conditions to tell if it's telephone, WeChat, whatsApp or Invalid
>
> WhatsApp = 'wta: 322424'
>
> telephone  = 'tel:2342423424'
>
> weChat = 'wec:ireaf_343'
>
> With a few more conditions for each

The second question ended up taking some time, but I still managed ti do both of them In 29mins which was pretty good.

### 2. Tech + HR interview

This round was a STAR + project discussion + CS Core interview. In my case the CS core question involved a Computer Networking question :
> When we hit a domain in the browser what happens next ?
> Ans: A get request is sent to a DNS server, which gives us the IP associated with the domain and then we are routed through servers and finally receive a response

*My answer was a little vague as I didn't know the complete answer but did know the basic so didn't want to be quiet or not answer*

Other than that we discussed some of my projects, and my experience at my older workplace.

### 3. Coding interview

```python
# In the pre-pandemic world (or when we get back in the office), we find it very challenging to find meeting rooms in 
# our Twilio offices and we want to solve that problem. We have the data of bookings for each conference room. For the sake of 
# this problem, we can assume that each meeting is one hour long. Each interval is one hour long. e.g. A session 2-10 consists
#  of 8 meetings of one hour each. (2,3), (3,4) ........ (9,10)

# Given this data (a set of booking timings across meeting rooms), find out the busiest hours of the day i.e when most the rooms are engaged concurrently.

# sample data set:

# room 1: 2-10
# room 2: 3-15
# room 3: 4-9
# room 4: 8-14
# room 5: 7-13
# room 6: 5-10
# room 7: 11-15

_input = [
    [2,10],
    [3,15],
    [4,9],
    [8,14],
    [7,13],
    [5,10],
    [11,15]
]


# O(n*m)+O(n) n=number of rooms, m=largest room interval
# def solution(testCase):
#     hours = [0]*24
#     for item in testCase:
#         start = item[0]
#         end = item[1]
#         for i in range(start-1,end):
#             hours[i]+=1
#     busy = max(hours)
#     print(f"BUSIEST HOUR => {hours.index(busy)+1}")
#     # print(f"FINAL {hours}")
#     pass


# O(n*m) n=number of rooms, m=largest room interval
def solution(testCase):
    hours = [0]*24
    busy = -1
    index = -1
    for item in testCase:
        start = item[0]
        end = item[1]
        for i in range(start-1,end):
            hours[i]+=1
            if busy<hours[i]:
                busy=hours[i]
                index = i
                print(hours,busy,index)
                
    print(f"Solution => {index+1}")
    pass


solution(_input)
```

I was able to get the a solution upto O(n) but I don't the solution to that. But in this interview they were more interested in compatibility and conversation during pair programming I say this because a friend of mine was able to get the solution quicker than me but was very quiet and didn't communicate a lot and hence didn't get selected.