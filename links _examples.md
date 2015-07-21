##  CRUD Step by step instructions
Mikes 7 step crud:
https://github.com/chi-bumblebees-2015/recipes-example-app/blob/end-of-lecture/app/controllers/recipes.rb
#### get all
#### get to new individual
####post new individual
####show individual by id
####get to edit form by id
####put edit form in DB by id
####delete indivudual by id 

https://github.com/chi-dragonflies-2015/phase-2-guide/blob/chicago/resources/step_by_step_crud.md

CRUD Moosetalk Example
https://github.com/thunderenlight/moosetalk

AJAX example

(https://github.com/chi-dragonflies-2015/ajaxifying-hacker-news-challenge/blob/pair-mccallumjack%2Cthunderenlight/public/js/application.js)
https://github.com/chi-dragonflies-2015/ajaxifying-hacker-news-challenge/tree/pair-alycit
```javascript
 <!--********************Ajax******************-->
 $(document).ready(function() {
  var $comment_list = $('ul.comment_list');

  $comment_list.on('submit', 'form.edit_comment', function(event) {
    event.preventDefault();
    var $target = $(event.target);

    $.ajax({
      type: 'PUT',
      url: $target.attr('action'),
      data: $target.serialize()
    }).done(function(response) {
      $target.closest('li').html(response);
    })
  })
  
$("body").on("click", "#new-caballo", function(event){
+		event.preventDefault();
+		var url = $("#new-caballo").attr("href");
+
+		var request = $.ajax({url: url});
+		
+		request.done(function(response){
+			$("#new-caballo").hide();
+			$("#caballo-list").append(response);
+		})
+	});
+
+	$("body").on("submit", "#caballo-form", function(event){
+		event.preventDefault();
+		var data = $("#caballo-form").serialize();
+		var url = $("#caballo-form").attr("action");
+		var type = "POST";
+
+		var request = $.ajax({
+			url: url,
+			type: type,
+			data: data
+		});
+
+		request.done(function(response){
+
+			$("#caballo-form").remove();
+			$("#end").append('<h3><a href="/caballos/' + response.id + '">' + response.name + '</a></h3>');
+			$("#new-caballo").show();
+		})
+	});
+
+	$("body").on("click", "#caballo h3 a", function(event){
+		event.preventDefault();
+		var horse = $(this);
+		var url = $(this).attr("href");
+		
+		var request = $.ajax({url: url});
+
+		request.done(function(response){
+			$(horse).append(response);
+		})
+	});
  
  
```

AR Associations 
(http://apidock.com/rails/ActiveRecord/Associations/ClassMethods/has_many)
(http://apidock.com/rails/ActiveRecord/Associations/ClassMethods/belongs_to)
  ```ruby
 <!--*************MODEL********************** -->
  class Physician < ActiveRecord::Base
  has_many :appointments
  has_many :patients, through: :appointments
end

class Appointment < ActiveRecord::Base
  belongs_to :physician
  belongs_to :patient
end

class Patient < ActiveRecord::Base
  has_many :appointments
  has_many :physicians, through: :appointments
end

<!--****************MIGRATION*******************-->
class CreateAppointments < ActiveRecord::Migration
  def change
    create_table :physicians do |t|
      t.string :name
      t.timestamps null: false
    end

    create_table :patients do |t|
      t.string :name
      t.timestamps null: false
    end

    create_table :appointments do |t|
      t.belongs_to :physician, index: true
      t.belongs_to :patient, index: true
      t.datetime :appointment_date
      t.timestamps null: false
    end
  end
end
https://socrates.devbootcamp.com/sql
rake generate:migration NAME=create_rooms
class CreateRooms < ActiveRecord::Migration
  def change
  	create_table :rooms do |t|
      t.integer :rate
      t.string :number
 	    t.references :hotel
      

      t.timestamps
    end
  end
end
<!--******************PASSWORD*********************-->

 def password
     @password ||= Password.new(password_digest)
   end

   def password=(new_password)
     @password = Password.create(new_password)
     self.password_digest = @password
   end

   def authenticate(password)
     self.password == Password.new(password)
   end
   <!---->This makes it possible to use just the word password when seeding/creating!!!! Keep as password_hash in migration

```
```javascript

var garden = {
  name: "Kula Botanical Garden",
  location: "Makawao",
  flowers : [],
  plant: function (flowers) {
    for(var i = 0; i < flowers.length; i++){  
    this.flowers.push(flowers[i]);
    };
  },
  selectByColor: function(color){
    var color_collector = []
    for(var i = 0; i < flowers.length; i++){
      if(this.flowers[i].color == color){
        color_collector.push(this.flowers[i]);
      };
    };
    return color_collector;
  },
var Flower = function(name, color){
  this.name = name;
  this.color = color;
};

Flower.prototype.identify = function(){
    var identify = "I am an " + this.name + " and I am " + this.color + "."
    return identify
  };
```

#### Crud and Ajax Talk 
(https://talks.devbootcamp.com/crud-and-ajax)
