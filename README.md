# -#pragma once
#include<cstddef>

float dotproduct1(const float* p1, const float* p2, size_t n);
float dotproduct2(const float* p1, const float* p2, size_t n);
float dotproduct3(const float* p1, const float* p2, size_t n);
float dotproduct4(const float* p1, const float* p2, size_t n);
float dotproduct5(const float* p1, const float* p2, size_t n);

#include<iostream>
#include<chrono>
#include"matoperation.hpp"

using namespace std;

#define TIME_START start = std::chrono::steady_clock::now();
#define TIME_END(NAME) end = std::chrono::steady_clock::now();\
        duration = std::chrono::duration_cast<std::chrono::milliseconds>
        (end - start).count();\
        cout << (NAME) << ": result = " \ 
        << ", duration = " << duration << "ms" << endl;
        
float dotproduct1(const float* p1, const float* p2, size_t n)
{
	float sum = 0.0f;
	for (int i = 0; i < n; i++)
		sum += (p1[i] * p2[i]);
	return sum;
}
        
int main(int argc, char ** argv)
{
	size_t nSize = 800,000,000;
	float * p1 = new float[nSize]();
	float * p2 = new float[nSize]();
	float result = 0.0f;
	
	p1[2] = 2.3f;
	p2[2] = 3.0f;
	p1[nSize-1] = 2.0f;
	p2[nSize-1] = 1.1f;
	
	auto start = std::chrono::steady_clock::now();
	auto end = std::chrono::steady_clock::now();
	auto duration = 0L;
	
	TIME_START
	result = dotproduct1(p1, p2, nSize);
	TIME_END("dotproduct1");
	
	delete []p1;
	delete []p2;
	
	return 0;
}
