# Лабораторная работа 0
У меня проблемы с загрузкой и конвертацией в пдф, поэтому я прикрепила ссылку на colab.  
https://colab.research.google.com/drive/1kf20bNkmGsOhVnD3PCzbLRGsw8-yxRsQ?usp=sharing  
Также просто ссылка (не colab).  
https://drive.google.com/file/d/1Iw88uv1sAShEftGfF969ZAT7Rjp-HY1R/view?usp=sharing  
Cсылка на данные.  
https://drive.google.com/file/d/1ftRxfSedP1742XNWRbBzRv82ZgWe8iGe/view?usp=sharing  
### Набор данных:  
 В нем 12 полей:  
1) id: ид человека (int64)  
2) gender: "Male", "Female" or "Other" - пол человека (object)  
3) age: возраст человека (float64)  
4) hypertension: гипертония: 0 - нет, 1 - есть (int64)
5) heart_disease: заболевания сердца: 0 - нет, 1 - есть (int64)  
6) ever_married: наличие супруга: да или нет (object)  
7) work_type: "children", "Govt_jov", "Never_worked", "Private" or "Self-employed" - занятость: ребенок, госслужащий, неработавший, частный или самозанятый (object)  
8) Residence_type: "Rural" or "Urban" - местность проживания - городская или сельская (object)  
9) avg_glucose_level: average glucose level in blood - уровень глюкозы (float64)  
10) bmi: body mass index - ИМТ (flloat64)  
11) smoking_status: "formerly smoked", "never smoked", "smokes" or "Unknown" - статус курения: раньше курил, никогда не курил, курит или неизвестно (object)  
12) stroke: 1 if the patient had a stroke or 0 if not - инсульт: 1 - был, 0 - не было (int64)  

### Преобразование данных
Из типа object  переделываем в категориальный:  
```
  df['smoking_status'] = df['smoking_status'].astype('category')  
  df['gender'] = df['gender'].astype('category')  
  df['Residence_type'] = df['Residence_type'].astype('category')  
  df['work_type'] = df['work_type'].astype('category')  
  df['ever_married'] = df['ever_married'].astype('category')  
```  
Также у bmi есть 3 пропущенных значения. Они заполнены медианой:  
```  
  df['bmi'] = df['bmi'].fillna((df['bmi'].median()))  
```  
У bmi также были выбросы, поэтому их нужно убрать:  
```
  df.drop(df[df['bmi'] > 47].index, inplace = True)
```  
### Постановка решаемых задач
С помощью этого датасета можно определить вероятность возникновения инсульта. Также можно определить уровень сахара в крови, гипертонию и наличие заболеваний сердца. 

### Проблемы
Я с самого начала не заметила, что в bmi есть выбросы, поэтому сначала зависимость между ИМТ и другими признаками не наблюдалась.  

### Выводы
![изображение](https://user-images.githubusercontent.com/71285888/165530988-d34dca84-48a0-43a4-acca-94d1dd0fad3a.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_001.png)  
![plot](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_002.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_003.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_004.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_005.png)   
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_006.png)    
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_007.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_008.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_009.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_010.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_011.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_012.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_013.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_014.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_015.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_016.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_017.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_018.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_019.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_020.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_021.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_022.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_023.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_024.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_025.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_026.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_027.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_028.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_029.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_030.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_031.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_032.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_033.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_034.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_035.png)   
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_036.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_037.png)  
![1](https://github.com/ivanova3600/LR0/blob/main/plot/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_038.png)  
  
Краткие выводы:    
1) Случаи инсульта повышаеются с увеличением возраста.   
2) Инсульт у мужчин встречается чаще.  
3) У детей и неработающих людей случаи инсульта минимальны.  
4) У людей с гипертонией инсульт возникает чаще, чем у людей без нее. Гипертония появляется обычно у людей 55+. При этом у мужчин гипертония всречается чаще. 
5) У людей с сердечными заболеваниями вероятность инсульта значительно выше. Сердечные заболевания появляется в основном у людей, старших 55 лет. У мужчин сердечные заболевания встречается чаще.  
6) У здоровых людей уровень глюкозы обычно меньше 110. При этом с увеличением возраста уровень глюкозы возрастает. У людей с инсультом он значительно выше. У людей с гипертонией уровень глюзы в среднем выше, чем у людей без нее.  
7) Средний ИМТ равен 25-30. У людей с ИМТ меньшим 20 инсульт практически не встречается (основная группа риска - ИМТ в районе 30-35). При этом у мужчин заметно меньше ИМТ, чем у женщин. ИМТ с возрастом постепенно увеличивается. Место жительствона ИМТ не влият. У людей с гипертонией ИМТ ниже 20 практически не опускается.   
8) Среди курящих и ранее куривших инсульты, гипертония и заболевания сердца встречаются значительно чаще, чем среди некурящих. Среди мужчин курящих больше, чем среди женщин. Сильной зависмости ИМТ от курения не наблюдается. Среди детей и никогда не работавших курящих практически нет, наибольший процент курящих - самозанятые. Люди, живущие в сельской местности, курят немного меньше.
9) Данные не коррелируются.
