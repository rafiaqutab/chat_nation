ChatRoom
=====
How to create a new user?
```ruby
User.create username: "must give a username"
```

How to create a new chat_room?
```ruby
ChatRoom.create title: "must have a title", initiating_user: User.find_by(name: "must have a creater - maybe admins can create in the future")
```

How to let a user communicate?
**Authorized user has access to different chat events**

```ruby
user = User.create(username: "rubygal")

user.enter_a_chat_room(pass_the_room)
user.leave_the_chat_room(pass_the_room)
user.send_message(pass_the_room, what_ever_he_wants_to_say)
user.send_high_five_to(pass_the_room, receiving_user_who_is_also_in_the_room)
```

The ChatRoom is the mediator and the users use the mediator to
communicate with each other. All the above chat events delegte
to the ChatRoom class.

DataAggregation
=====
A user that has access to a chat room can view data based on a granularity level

GranularityLevel module gives various levels: minute_by_minute, hourly, weekly, daily...etc
In order to aggregate chatroom data:

```ruby
DataAggregator.group_by(granularity_level, pass_the_chat_room)
```
