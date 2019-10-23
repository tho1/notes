dart notes

* news
https://medium.com/dartlang

* old news.
https://news.dartlang.org/

* dart academy
https://dart.academy/


Notes from Language tour

https://dart.dev/guides/language/language-tour

* dynamic -- for abstract type. no inference. no types expected

* identifier starting with _ is consider private to the library

* every class defines an interface implicitly.

* variable definitions.
	
	var name = 'Bob';
	dynamic name = 'Bob';
	String name = 'Bob'; 
	
	
* difference between const and final?
	const variables are implicitly final.
	Instance variables can be final but not const.
	const for compile time constants
	
* type
	see https://dart.dev/guides/language/language-tour#type-test-operators

* List	https://dart.dev/guides/language/language-tour#lists
	zero based indexing, spread operator, null aware operator
	
	
	var list = [1, 2, 3];
	var list2 = [0, ...list];
	assert(list2.length == 4);
	
	
	var list;
	var list2 = [0, ...?list];
	assert(list2.length == 1);
	
	
	
* String
	var s = r'In a raw string, not even \n gets special treatment.';   
	support concatenation, ''' for multi line string

	collection if and colleciton for, very nice syntactic sugar.
	
	var nav = [
		  'Home',
		  'Furniture',
		  'Plants',
		  if (promoActive) 'Outlet'
		];
	
	
* Sets
	denotes by {} e.g. var elements = <String>{};
	add, addAll 
	
* Runes	
		32 code points.  internationalized string.
		Runes input = new Runes(
      '\u2665  \u{1f605}  \u{1f60e}  \u{1f47b}  \u{1f596}  \u{1f44d}');
		print(new String.fromCharCodes(input));
		
* Symbols
	compile time constants.
	#radix
	
* Functions
	optional, named, and positional parameters
	see https://pub.dev/packages/args to parse arguments.
	
	Lexical closures -> A closure is a function object that has access to variables in its lexical scope, 
	
		/// Returns a function that adds [addBy] to the
		/// function's argument.
		Function makeAdder(num addBy) {
		  return (num i) => addBy + i;
		}

		void main() {
		  // Create a function that adds 2.
		  var add2 = makeAdder(2);

		  // Create a function that adds 4.
		  var add4 = makeAdder(4);

		  assert(add2(3) == 5);
		  assert(add4(3) == 7);
		}
		
				
* Checking code
	extra_pedantic compare to pedantic
	
	
* OOP 
	abstract, implicit interface
	@override to override an instance method.
	
	mixin: reusing a class’s code in multiple class hierarchies.    
		with keyword followed 1 or more mixin names.
		defines a new class with mixin and declares no constructors
	

	Factory constructor
		Use the factory keyword when implementing a constructor that doesn’t always create a new instance of its class. For example, a factory constructor might return an instance from a cache, or it might return an instance of a subtype.
		
		class Logger {
		  final String name;
		  bool mute = false;

		  // _cache is library-private, thanks to
		  // the _ in front of its name.
		  static final Map<String, Logger> _cache =
			  <String, Logger>{};

		  factory Logger(String name) {
			return _cache.putIfAbsent(
				name, () => Logger._internal(name));
		  }

		  Logger._internal(this.name);

		  void log(String msg) {
			if (!mute) print(msg);
		  }
		}


* Generics

* Async, Wait, Future, Stream
	https://dart.dev/tutorials/language/streams
	https://dart.dev/codelabs/async-await
		
* Isolates
	almost like running its own greenthreads, have its own heaps.
	https://api.dart.dev/stable/dart-isolate
	https://flutter.dev/docs/cookbook/networking/background-parsing
	
	https://itnext.io/by-design-dart-is-a-single-threaded-programming-language-924c41e5c135
	
* Typedefs
	 

* ffi
	dart.ffi to call native C library.

		
* functional programming.
values.skip(1).take(3).map(scream).forEach(print);

async, sync, yield

Library tour
