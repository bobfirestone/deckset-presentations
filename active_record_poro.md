# [fit]AR vs PORO

___

# ActiveRecord is an ORM

* ORM = Object Relational Mapping
* AR gives developers an abstraction layer for the interaction between a SQL database & application
* No writing SQL queries!
* AR gives developers a lot out of the box

___

AR class

```ruby
    class Post < ActiveRecord::Base
      validates :title, presence: true
      validates :body, presence: true

      has_one :author
      has_many :comments
    end
```

___

# Easy access to DB records
```ruby
    class PostController < ApplicatonController
      def index
        @posts = Post.all
      end

      def show
        @post = Post.find(params[:id])
      end

      def posts_by_author
        @posts = Post.where(author_id: params[:author_id])
      end
    end
```

---

# Ruby != Ruby on Rails

Most rails apps are ActiveRecord centric

*In CRUD apps where the objects you work with map directly to database tables AR has you covered*

__AR classes tend to get bloated & quickly__

---

# [fit]AR + PORO

___

# Plain Old Ruby Object
```ruby
    class Post
      attr_accessor :title, :body
      def initialize(attrs)
        @title = attrs[:title]
        @body  = attrs[:body]
      end
    end
```
*An instantiated PORO live in system memory until they are dereferenced and garbage collected*
___

# ActiveModel AR magic in a PORO
```ruby
    class Post
      include ActiveModel::Validations

      attr_accessor :title, :body

      validates_presence_of :title, :body

      def initialize(attrs)
        @title = attrs[:title]
        @body  = attrs[:body]
      end
    end
```

___

# [fit]Mix & Match

___

![](http://images4.alphacoders.com/227/227454.jpg)
# [fit]Who wants to see some code?

---

![fit](http://upload.wikimedia.org/wikipedia/commons/6/6f/Romeo_Juliet.jpg)

# Balthasar
* A secret messaging app
* Only the encrypted message is stored
* Must enter correct PW to retrieve message
* Never stores the password

*Balthasar is the messenger in Romeo & Juliet*

___

# [fit]Questions
