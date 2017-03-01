# InterX

Created on Wed Mar 01 10:00:09 2017

@author: Kelsey N. Lucas

Translation of NS's InterX for Matlab into Python.
Original Available at: https://www.mathworks.com/matlabcentral/fileexchange/22441-curve-intersections/content/InterX.m


Python translation (c) 2017, Kelsey N. Lucas
Original Matlab code Copyright (c) 2009, NS
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are
met:

    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.
    * Redistributions in binary form must reproduce the above copyright
      notice, this list of conditions and the following disclaimer in
      the documentation and/or other materials provided with the distribution

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN
CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
POSSIBILITY OF SUCH DAMAGE.




InterX Intersection of curves

    Input:
    -L1x - Pandas dataframe of x-values for curve 1
    -L1y - Pandas dataframe of y-values for curve 1
    Optional input:
    -L2x - Pandas dataframe of x-values for curve 2
    -L2y - Pandas dataframe of y-values for curve 2
    
    Returns:
    -P - a Pandas dataframe containing two columns - xs, the x-values of 
    intersection points, and ys, the y-values of intersection points.  If no 
    intersection is found, xs and ys are both None.


   P = InterX(L1x,L1y,L2x,L2y) returns the intersection points of two curves L1 
   and L2. The curves L1,L2 can be either closed or open.

   P = InterX(L1x,L1y) returns the self-intersection points of L1. To keep
   the code simple, the points at which the curve is tangent to itself are
   not included.
   

   Author : NS
   Translated from Matlab code Version: 3.0, 21 Sept. 2010
   Translator: Kelsey N. Lucas
   Translation version: 1.0, Mar 2017

   Two words about the algorithm: Most of the code is self-explanatory.
   The only trick lies in the calculation of C1 and C2. To be brief, this
   is essentially the two-dimensional analog of the condition that needs
   to be satisfied by a function F(x) that has a zero in the interval
   [a,b], namely
           F(a)*F(b) <= 0
   C1 and C2 exactly do this for each segment of curves 1 and 2
   respectively. If this condition is satisfied simultaneously for two
   segments then we know that they will cross at some point. 
   Each factor of the 'C' arrays is essentially a matrix containing 
   the numerators of the signed distances between points of one curve
   and line segments of the other.
