#+- SVN Keywords ----------------------------------------------------+
#|                                                                   |
#| $HeadURL::                                                      $:|
#|     $Rev::                                                      $:|
#|    $Date::                                                      $:|
#|  $Author::                                                      $:|
#|                                                                   |
#+-------------------------------------------------------------------+


APP=wizualizacja_robota

__start__: obj ./${APP}
	rm -f core.* core; ./${APP}

# Tworzy katalog "obj" gdy go nie ma
# 
obj:
	mkdir -p obj

./${APP}: obj/main.o obj/main.o obj/lacze_do_gnuplota.o
	g++ -o ./${APP} obj/main.o obj/lacze_do_gnuplota.o

obj/main.o: src/main.cpp inc/lacze_do_gnuplota.hh 
	g++  -Iinc -W -Wall -pedantic -c -o obj/main.o src/main.cpp

obj/lacze_do_gnuplota.o: src/lacze_do_gnuplota.cpp inc/lacze_do_gnuplota.hh
	g++  -Iinc -W -Wall -pedantic -c -o obj/lacze_do_gnuplota.o src/lacze_do_gnuplota.cpp

doc:
	cd ./dox;  make
	@echo
	@echo  "  Dokumentacja zostala umieszczona w katalogu dox/doc/html"
	@echo

clean:
	rm -f obj/* ./${APP}_rozszerzony ./${APP} core.* core

help:
	@echo
	@echo "  Lista podcelow dla polecenia make"
	@echo 
	@echo "        - (wywolanie bez specyfikacji celu) wymusza"
	@echo "          kompilacje i uruchomienie programu."
	@echo "  clean - usuniecie produktow kompilacji i konsolidacji"
	@echo "  doc   - powoduje generowanie dokumentacji"
	@echo "  help  - wyswietla niniejsza informacje"
	@echo
	@echo
	@echo " Przykladowe wywolania dla poszczegolnych wariantow. "
	@echo "  make           # kompilacja i uruchomienie programu."
	@echo "  make clean     # usuwa produkty kompilacji."
	@echo "  make doc       # generuje dokumentacje w doc/html"
	@echo
