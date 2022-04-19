# Лабораторная работа 0
Набор данных:  
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

  df['smoking_status'] = df['smoking_status'].astype('category')  
  df['gender'] = df['gender'].astype('category')  
  df['Residence_type'] = df['Residence_type'].astype('category')  
  df['work_type'] = df['work_type'].astype('category')  
  df['ever_married'] = df['ever_married'].astype('category')  
  
Также у bmi есть 3 пропущенных значения. Они заполнены медианой:  
  
  df['bmi'] = df['bmi'].fillna((df['bmi'].median()))  
  
У bmi также были выбросы, поэтому их нужно убрать:  

  df.drop(df[df['bmi'] > 47].index, inplace = True)
  
### Постановка решаемых задач
С помощью этого датасета можно определить вероятность возникновения инсульта. Также можно определить уровень сахара в крови, гипертонию и наличие заболеваний сердца. 

### Проблемы
Я с самого начала не заметила, что в bmi были выбросы, поэтому сначала зависимость между ИМТ и другими признаками не наблюдалось.  

### Выводы
Из построенных графиков

