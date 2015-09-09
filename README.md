ORM for Pyth*on*Rails
===

This ORM idea is to **simplify syntax** of queries to any DB.


Syntax
---

Examples of syntax:

```python
# we will use Blog model for examples

# get data by one field
>>> Blog.get_by_name(blog_name)
>>> Blog.get_by_id(blog_id)

# filter data to create queryset
>>> queryset = Blog.filter(name=blog_name, user=current_user)
>>> queryset.filter(exclude_user=blocked_user)

# get first, last or all records from queryset
>>> Blog.all    # or "queryset.all"
>>> Blog.first  # or "queryset.first"
>>> Blog.last   # or "queryset.last"

# create / delete / update - object
>>> blog = Blog.create(name='Super tech blog')
>>> blog.update(name='Tech blog')
# update() is equal to next two lines
>>> blog.name = 'New tech blog'
>>> blog.save()
>>> blog.delete()

# create / delete / update - queryset
>>> queryset = Blog.filter(user=blocked_user)
>>> queryset.update(date_modify=now())
>>> queryset.delete()

# limit queryset
>>> records = queryset[0]    # the same as "queryset.first"
>>> records = queryset[:10]  # get first 10 records
>>> records = queryset[5:10] # get records from 6 to 10 (6, 7, 8, 9)
>>> records = queryset[5:]   # get records from 6

# get changed fields
>> blog = Blog.create(name='New blog')
>> blog.name = 'New age blog'
>> blog.changed_fields
['name']  # what about auto-modified field 'date_change'?
```
