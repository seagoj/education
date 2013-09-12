# Backbone.js

## The Anatomy of Backbone.js
* [Level 1: Introduction](#level-1-introduction)
* [Level 2: Models](#level-2-models)

### [Level 1: Introduction](http://backbone.codeschool.com/levels/1)
* Backbone is a client side MVC

#### Model Class
    // Create a model class
    var TodoItem = Backbone.Model.extend({});

#### Model Instance
	// Create model instance
	var todoItem = new TodoItem(
		{ description: 'Pick up milk', status: 'incomplete', id:1 }
	);

	// Retrieve data from the model
	todoItem.get('description')

	// Set a value in the model
	todoItem.set({status: 'complete'});

	// Sync to the server
	todoItem.save();

#### View Class
	// Create a view class (incomplete)
	var Todoview = Backbone.View.extend({});

#### View Instance
	// Create view instance
	var todoView = new TodoView({model: todoItem})

#### Define Render
	// Every view instance requires a render function
	var TodoView = Backbone.View.extend({
		render: function() {
			var html = '<h3>' + this.model.get('description') + '</h3>';
			$(this.el).html(html);
		}
	});

#### Render the view
	// renders view into $(this.el)
	todoView.render();
	// logs to console
	console.log(todoView.el);

### [Level 2: Models](http://backbone.codeschool.com/levels/2)
