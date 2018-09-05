This file holds the tests that you create. Remember to import the python file(s)
you wish to test, along with any other modules you may need.
Run your tests with "python3 ok -t --suite SUITE_NAME --case CASE_NAME -v"
--------------------------------------------------------------------------------

Suite 1

	>>> from ants import *

	Case Example
		>>> x = 5
		>>> x
		5

Suite 15

	>>> # General FireAnt Test
	>>> from ants import *
	>>> hive, layout = Hive(AssaultPlan()), dry_layout
	>>> dimensions = (1, 9)
	>>> colony = AntColony(None, hive, ant_types(), layout, dimensions)
	>>> place = colony.places['tunnel_0_4']
	>>> bee = Bee(3)
	>>> bee2 = Bee(10)
	>>> ant = FireAnt()
	>>> place.add_insect(bee)
	>>> place.add_insect(bee2)
	>>> place.add_insect(ant)

	Case 1
		>>> place.ant is ant
		True
	
	Case 2
		>>> len(place.bees)
		2
	
	Case 3
		>>> ant.reduce_armor(1) # Poke the FireAnt
		>>> bee.armor             # Bee should not get damaged
		0
		
	Case 4		
		>>> ant.reduce_armor(1) # Poke the FireAnt
		>>> bee2.armor
		7
		
	Case 5
		>>> ant.reduce_armor(1) # Poke the FireAnt
		>>> ant
		FireAnt(0, None)
		
		>>> ant.armor
		0
		
	Case 6
		>>> ant.reduce_armor(1) # Poke the FireAnt
		>>> place.ant is ant      # The FireAnt should be destoried 
		False
