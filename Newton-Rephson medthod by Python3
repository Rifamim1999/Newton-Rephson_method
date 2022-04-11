# -*- coding: utf-8 -*-
"""
Created on Fri Apr  8 01:44:21 2022

@author: USER
"""

import numpy as np
import math
import xlwt
from xlwt import Workbook
 
def func(x):
    fx = -(.6*x*x)+(2.4*x)+5.5
    return fx
'''The float value can not be accessed using the index. If you attempt to change the float value using index, 
the error TypeError: ‘float’ object does not support item assignment will be thrown in python.
'''

run = True 
while run:
    xl = float(input("Enter the first initial guess: "))
    xu = float(input("Enter the second initial guess: "))
    fxl = func(xl)
    fxu = func(xu)
    if fxl*fxu < 0:
        run = False
        
ite = int(input("Enter the number of iteration: "))
err = float(input("Enter the tolarable error: "))

#initialization of arrays 
x_l = np.zeros([ite])
x_u = np.zeros([ite])
f_xl = np.zeros([ite])
f_xu = np.zeros([ite])
error = np.zeros([ite])
num_ite = np.zeros([ite])
x_mid = np.zeros([ite])
f_xmid = np.zeros([ite])

#putting the values of first index of arrays
x_l[0] = xl
x_u[0] = xu
f_xl[0] = fxl
f_xu[0] = fxu

for i in range(ite):
    num_ite[i] = i+1
    x_mid[i] = (x_l[i] + x_u[i])/2
    
    f_xl[i] = func(x_l[i])
    f_xu[i] = func(x_u[i])
    f_xmid[i] = func(x_mid[i])
    if i>0:
        error[i] = ((x_mid[i]-x_mid[i-1])/x_mid[i])*100
    
    #termination conditions
    if all([i>0 ,abs(error[i])<err]):
        break
    if f_xmid[i] ==0:
        break
    if num_ite[i] == ite-1:
        break
    
    #replacement of new values
    
    if all ([f_xl[i]>0, f_xmid[i]>0]):
        x_l[i+1] = x_mid[i]
        x_u[i+1] = x_u[i]
    if all([f_xl[i]<0, f_xmid[i]<0]):
        x_l[i+1] = x_mid[i]
        x_u[i+1] = x_u[i]
    if all([f_xu[i]>0, f_xmid[i]>0]):
        x_u[i+1] = x_mid[i]
        x_l[i+1] = x_l[i]
    if all([f_xu[i]<0, f_xmid[i]<0]):
        x_u[i+1] = x_mid[i]
        x_l[i+1] = x_l[i]
print("The root is : ", x_mid[i])

#writing the results in excel
wb = Workbook()

sheet1 = wb.add_sheet('Sheet1')
iteration = i
#writing on excel
sheet1.write(0,0,'Number of iteration')
sheet1.write(0,1,'x_l')
sheet1.write(0,2,'x_u')
sheet1.write(0,3,'f(x_l)')
sheet1.write(0,4,'f(x_u)')
sheet1.write(0,5,'x_c')
sheet1.write(0,6,'f(x_c)')
sheet1.write(0,7,'Relative error')

for n in range(iteration):
    sheet1.write(n+1, 0, num_ite[n])
    sheet1.write(n+1, 1, x_l[n])
    sheet1.write(n+1, 2, x_u[n])
    sheet1.write(n+1, 3, f_xl[n])
    sheet1.write(n+1, 4, f_xu[n])
    sheet1.write(n+1, 5, x_mid[n])
    sheet1.write(n+1, 6, f_xmid[n])
    sheet1.write(n+1, 7, error[n])

sheet1.write(n+4,2,'The')
sheet1.write(n+4,3,'root')
sheet1.write(n+4,4,'is')
sheet1.write(n+4,5,x_mid[i])

#saving the sheet
wb.save('Problem 5.1 (b).xls')
