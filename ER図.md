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



entity "四択問題テーブル" as four_choice <four_choice> <<T,TRANSACTION_MARK_COLOR>> {
+ for-choice_id [PK]
--
for-choice_sentence
choice1
choice2
choice3
choice4
four-choice_explanation
member_id [FK]
}



entity "マルバツ問題テーブル" as two_choice <two_choice> <<T,TRANSACTION_MARK_COLOR>> {
+ two-choice_id [PK]
--
two-choice_id
two-choice_sentence
true-answer
false-answer
two-choice_explanation
member_id [FK]
}

member }|-ri-|{four_choice
member }|-le-|{two_choice

```
