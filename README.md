# Forms and Resources
## CRUD Rails Drills

## Intro

| Objectives |
| :---- |
| Review **CRUD** in the context of a Rails application, especially **Updating** and **Deleting** a resource. |
| Examine **form helpers** and **partials** (if time permits) in a Rails Application. |
| Apply styling and [**Bulma**](https://bulma.io/documentation/) to our site to create a custom layout. |


### You Already Know

* Routing requests to a controller method
	* **INDEX**
	* **NEW** 
	* **CREATE**
	* **EDIT**
	* **UPDATE**
	* **DESTROY**
* RESTful resources
* Basic HTML Forms 	

### Outline

| Background |
| :--- |
| A bog is a mire that accumulates peat, a deposit of dead plant material—often mosses. |

Researchers are collecting data on a local bog and need an app to quickly record field data. Our goal is to create a **Bog App**. 

When I hear bog, I think of this ... "do or do not, there is no try" – Yoda

![luke](http://1.bp.blogspot.com/-Aa0TuXoIMoU/T4M7_GbT8uI/AAAAAAAAin8/lcUZkoqoJM4/s1600/Yoda-and-Luke.jpg)

#### Part I: Review and Apply Form Helpers

* Drop in [Bulma](https://bulma.io/documentation/)
* Create a **Creature** model.
	* verify it works in console. Hint: rails c
* Setup a **`/creatures/`** index
	* iterate over each creature
* Setup a **`/creatures/new`** and **CREATE**
	* Use form helpers with a new `Creature`
* Setup a **`/creatures/:id`** to show a particular `creature`

#### Part II: Setup Edit, Update, and Delete

* Setup a **`/creatures/:id/edit`** and **UPDATE**
* Setup a **Delete**


## Part I: Review and Refactor

### Here are a few steps to get you going

* `$ rails new -d postgresql bog_app`
* `$ cd bog_app`
*  NOTE: `rails db:create`
*  Generate your models, e.g. rails generate model creature
*  Open the application in your text editor
* `$ rails s`

Now our app is up and running, [localhost:3000](localhost:3000/). 

### Drop in Bulma

Start by using the [bulma rails](https://github.com/joshuajansen/bulma-rails)

### Create A Creature 

In terminal, we create our `Creature` model using a rails generator as follows,

	$ rails g model creature name description
	$ rake db:migrate

#### Verify it works

We go straight into terminal to enter *rails console*.

	$ rails console

	> Creature.create({name: "Yoda", description: "Green little man"}) 
	=> #<Creature ....>

*This will avoid issues later with `index` trying to render Creatures that aren't there.*
 
#### Seeds

`db/seeds.rb`
	
	 Creature.create({name: "Luke", description: "One-handed Jedi"})
	 Creature.create({name: "Darth Vader", description: "Evil father of Luke."})
	 Creature.create({name: "Cookie Monster", description: "Cookie-eating maniac"})
	 Creature.create({name: "Swamp Thing", description: "Covered in moss"})
	 Creature.create({name: "Alien", description: "Lizard thing with a mouth inside its mouth and acid for blood"})
	 Creature.create({name: "Bigfoot", description: "Man-ape living in the forest.  Very big feet."})
	 Creature.create({name: "Dracula", description: "Good dreser.  Vants to suck your blood."})

Then, run `$ rails db:seed` in console.

### Routes


Go to `config/routes.rb` and inside the routes block erase all the commented text and add the following:

`config/routes.rb`

	Rails.application.routes.draw do
		root to: 'creautres#index'
		resources :creatures
	end

Your `routes.rb` will just be telling your app how to connect *HTTP* requests to a **Controller**. Then, run `rails routes` to see a list of all the routes available to you.


#### Start by Generating a Creatures Controller

Let's begin with the following 

	$ rails g controller creatures

which is a generator for creating our controller and fill out the rest of the CRUD functionality.

### Partials

Create a form partial and render it to the `edit` and `new` view pages. 

## This homework is due 🚨 12PM (MIDNIGHT) TONIGHT🚨
