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



entity "メンバーテーブル" as member <member> <<M,MASTER_MARK_COLOR>> {
+ member_id [PK]
--
member_id
member_name
member_pass
member_mail
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



entity "マルバツテーブル" as two_choice <two_choice> <<T,TRANSACTION_MARK_COLOR>> {
+ two-choice_id [PK]
--
two-choice_id
true-answer
question_id [FK]
}


entity "解答テーブル" as answer <answer> <<T,TRANSACTION_MARK_COLOR>> {
+ two-choice_id [PK]
+ member_id [PK]
--
two-choice_id [FK]
member_id [FK]
answer
time
}


entity "タイプテーブル" as type <type> <<T,TRANSACTION_MARK_COLOR>> {
+ question_id [PK]
--
question_id
type
two-choice_sentence
two-choice_explanation
member_id [FK]
}

answer ||-d-o{ type
type }|-ri-|{four_choice
type }|-le-|{two_choice

```
