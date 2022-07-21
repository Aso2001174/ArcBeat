```uml
@startuml
!define Color_M Blue
!define Color_R Red
!define Color_C DeepSkyBlue



skinparam class {
BackgroundColor CadetBlue
BorderColor white
ArrowColor black
IconFontColor black
}



!define MASTER_MARK_COLOR yellow
!define TRANSACTION_MARK_COLOR yellowgreen



package "クイズメーカー" as target_system{



entity "ユーザーテーブル" as users <users> <<M,MASTER_MARK_COLOR>> {
+ id [PK]
--
id
name
pass
mail
deleted_at
}



entity "4択テーブル" as four_choice <four_choice> <<T,TRANSACTION_MARK_COLOR>> {
+ four-choice_id [PK]
--
four-choice_id
choice1
choice2
choice3
choice4
question_id [FK]
}


entity "解答テーブル" as answers <answers> <<T,TRANSACTION_MARK_COLOR>> {
+ id [PK]
+ user_id [PK]
--
id [FK]
user_id [FK]
category
answer_number
correct_answer
}


entity "問題テーブル" as questions <type> <<T,TRANSACTION_MARK_COLOR>> {
+ id [PK]
--
id
category
question
explanation
user_id [FK]
answer
title
}

answers ||-ri-o{users
answers ||-d-o{questions
questions |o-ri-||four_choice
questions ||-up--{users

```
