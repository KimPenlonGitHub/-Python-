#存储数据基础知识：
	1、CSV写入与读取——引用CSV模块；
	2、Excel写入与读取——引用openpyxl模块；
	
一、CSV文件写入与读取：
#写入的步骤：
	0、创建文件——调用open（）函数；
	1、创建对象——借助writer（）函数；
	2、写入内容——调用writer对象的writerow（）方法；
	3、关闭文件——close（）；
#读取的步骤：
	0、打开文件——调用open（）函数；
	1、创建对象——借助reader（）函数；
	2、读取内容——遍历reader对象；
	3、打印内容——print（）；
	
#csv写入的代码：

import csv
csv_file = open('demo.csv','w',newline='')
writer = csv.writer(csv_file)
writer.writerow(['电影','豆瓣评分'])
csv_file.close()

#csv读取的代码：

import csv
csv_file = open('demo.csv','r',newline='')
reader=csv.reader(csv_file)
for row in reader:
    print(row)

二、Excel文件写入与读取：
#写入的步骤：
	0、创建工作簿——利用openpyxl.Workbook（）创建workbook对象；
	1、获取工作表——借助workbook对象的active属性；
	2、操作单元格——单元格：sheet['A1']；一行：append（）；
	3、保存工作簿——save（）；
#读取的步骤：
	0、打开工作簿——利用openpyxl.load_workbook（）创建workbook对象；
	1、获取工作表——workbook对象的键，wb['sheet']；
	2、读取单元格——借助单元格value属性，sheet['A1'].value；
	3、打印单元格——print（）；

#Excel写入的代码：

import openpyxl 
wb = openpyxl.Workbook() 
sheet = wb.active
sheet.title ='new title'
sheet['A1'] = '漫威宇宙'
rows = [['美国队长','钢铁侠','蜘蛛侠','雷神'],['是','漫威','宇宙', '经典','人物']]
for i in rows:
    sheet.append(i)
print(rows)
wb.save('Marvel.xlsx')

#Excel读取的代码：

import openpyxl
wb = openpyxl.load_workbook('Marvel.xlsx')
sheet = wb['new title']
sheetname = wb.sheetnames
print(sheetname)
A1_value = sheet['A1'].value
print(A1_value)
	

