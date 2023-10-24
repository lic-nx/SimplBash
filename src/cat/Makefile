OPT = -std=c11 -Wall -Werror -Wextra
CI = gcc
CC = $(CI) $(OPT)

all :s21_cat 
	rm -rf *.o

s21_cat: s21_cat.o
	$(CC) s21_cat.o -o s21_cat

s21_cat.o: s21_cat.c 
	$(CC) -c $< -o $@

clean: 
	rm -rf *.o
	rm -rf s21_cat
	rm -rf *.log

leaks: all
	leaks -atExit -- ./s21_cat

check: s21_cat
	sh test_func_cat.sh
	clang-format -style=google -n *.c
	clang-format -style=google -n *.h
	

rebuild:
	rm -rf *.o 
	rm s21_cat
	make
