# pythontest
#-*- coding:utf-8 -*-
import difflib
import sys
import os

def compare(file1,file2,file3):
    try:
        f1=open(file1,'r')
        l1=f1.read().splitlines()
        f2=open(file2,'r')
        l2=f2.read().splitlines()
        f1.close()
        f2.close()
    except IOError as error:
        print("Error:%s", error)
    if os.path.exists(file3):
        fp=open(file3,'w+')
        fp=fp.truncate()
        result=difflib.Differ()
        diff=result.compare(l1,l2)
        fp.write(diff)
        print( '\n'.join(diff))
        fp.write('compare completly!')
        fp.close()

compare("C:\\Users\\Public\\file1.txt","C:\\Users\\Public\\file2.txt","C:\\Users\\Public\\file3.txt")
