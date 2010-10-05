!SLIDE subsection

# Object Model #

!SLIDE

# Classes and Objects #

	@@@ ruby
	class Canadian < Object
	  def speak
	    puts "eh?"
	  end	  
	end

	Canadian.new.speak
	# eh?

!SLIDE

# Simple Inheritance#

	@@@ ruby
	class Winnipegger < Canadian
	  def speak
	    puts "brrr..."
	  end	  
	end

	Canadian.new.speak
	# eh?
	Winnipegger.new.speak
	# brrr...

!SLIDE

# Simple Inheritance #

Diagram of object model for that example goes here. Winnipegger ->
Canadian -> Object

!SLIDE

# Singleton Methods #

	@@@ruby
	newfie = Canadian.new
	def newfie.speak
	  "[untranscribable], eh?"
	end
	newfie.speak
	# [untranscribable], eh? 

!SLIDE 

# What is a class? #

	@@@c
	struct RBasic {
	    VALUE flags;
	    VALUE klass;
	};
	
	typedef struct {
	    VALUE super;
	    struct st_table *iv_tbl;
	} rb_classext_t;
	
	struct RClass {
	    struct RBasic basic;
	    rb_classext_t *ptr;
	    struct st_table *m_tbl;
	    struct st_table *iv_index_tbl;
	};

!SLIDE

# What is a class? #

	@@@c
	/* sort of like... */
	struct RClass {
	  VALUE superclass;
	  struct st_table *instance_variables;
	  struct st_table *methods;
	  /* plus some other stuff */
	};

# What is a class? # 

(diagram: a few classes with pointers to method tables)
