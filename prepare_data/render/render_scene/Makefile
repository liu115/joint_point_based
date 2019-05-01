#CPPFLAGS= -Wall -O2 -std=c++14 -fopenmp -lpthread
#EIGEN_INC=/tmp3/hychiang/eigen-eigen-b3f3d4950030
#UTILS=render.cpp tinyply.cpp
#MAIN_CPP=main.cpp
#ALL:
#	g++ $(CPPFLAGS) $(MAIN_CPP) $(UTILS) -I $(EIGEN_INC) -o main


CPPFLAGS=-Wall -O2 -std=c++14
EIGEN_INC=/tmp3/hychiang/eigen-eigen-b3f3d4950030
INC=/home/master/05/hychiang/.local/include/
LIB=/home/master/05/hychiang/.local/lib/

#OBJECTS=main.o render.o tinyply.o

#all:
#	g++ $(CPPFLAGS) main.cpp tinyply.cpp render.cpp -I $(INC) -I $(EIGEN_INC) -o main -L $(LIB) -lz -lOpenImageIO 
sfm_pose: sfm_pose.o render.o tinyply.o
	g++ $(CPPFLAGS) sfm_pose.o render.o tinyply.o -o $@ -L $(LIB) -fopenmp -lpthread -lz -lopenblas -llapack -lOpenImageIO
	rm *.o

sfm_pose.o: sfm_pose.cpp
	g++ $(CPPFLAGS) -I $(INC) -I $(EIGEN_INC) -c $< -o $@ -fopenmp

syn_pose: syn_pose.o render.o tinyply.o
	g++ $(CPPFLAGS) syn_pose.o render.o tinyply.o -o $@ -L $(LIB) -fopenmp -lpthread -lz -lopenblas -llapack -lOpenImageIO 
	rm *.o

syn_pose.o: syn_pose.cpp
	g++ $(CPPFLAGS) -I $(INC) -I $(EIGEN_INC) -c $< -o $@ -fopenmp

render.o: render.cpp
	g++ $(CPPFLAGS) -I $(INC) -I $(EIGEN_INC) -c $< -o $@

tinyply.o: tinyply.cpp
	g++ $(CPPFLAGS) -c $< -o $@ 

clean:
	rm syn_pose sfm_pose