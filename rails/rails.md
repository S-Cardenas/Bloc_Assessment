##**Question**
Hey mentor,

I am starting to understand associations, but I'm still confused about through. What's the practical difference between a has_many and a has_many :through? What about has_one :through? When do I use them?

-Student

##**Response**

Hi Student,

This is a common grievance that many Rails developers go through in the beginning. Fortunately,
they all eventually become masters of it and so will you.

Let's say for example that we have three models: `Teacher`, `Course` and `Students`.

```
Teacher
Course
Students
```

In "simple" english we would describe the relationship between the three models as so:

A Teacher `has_one :course`
A course `belongs_to :teacher`
A course `has_many :students`
Student `belongs_to :course`

Because of our associations we can also say:

A teacher `has_many :students, through: :course`
A student `has_one :teacher, through: :course`

What `through: ` allows you to do is to write cleaner code by delegating model relationships to other models.
For example, instead of writing `Teacher.course.students` we can now write `Teacher.students` to find all the
students that belong to a particular teacher. Additionally, instead of writing `Students.all.first.course.teacher` to find the teacher of the first student, we can write `Students.all.first.teacher`.

##**Recap**
1. Use `has_many , through:` to create a one-to-many model relationship by delegating through: another model.
2. Use `has_one , through:` to create a one-to-one model relationship by delegating through: another model.

Give it a shot and let me know if you have any further questions. You'll be a master in no time.

Best regards,

Stefan
