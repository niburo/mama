# README


## users テーブル

|      Column        |  Type  |   Options   |
| ------------------ | ------ | ----------- |
| nickname           | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |
| last_name          | string | null: false |
| first_name         | string | null: false |
| age                | string | null: false |
| children           | string | null: false |
| birthday           | date   | null: false |
| profiles           | string | null: false |
### Association
  has_many :mama
  has_many :messages
  has_many :room_users
  has_many :rooms, through: :room_users

## rooms テーブル

|      Column        |  Type      |   Options   |
| ------------------ | ---------- | ----------- |
| name               | string     | null: false |
| nickname           | string     | null: false |
### Association
  has_many :room_users
  has_many :users, through: :room_users, dependent: :destroy
  has_many :messages, dependent: :destroy


## room users テーブル

|      Column        |  Type      |   Options   |
| ------------------ | ---------- | ----------- |
| room               | references | key: true   |
| user               | references | null: false |
| nickname           | string     | null: false |
### Association
  belongs_to :room
  belongs_to :user


## messages テーブル

|      Column        |  Type      |   Options   |
| ------------------ | ---------- | ----------- |
| room               | references | key: true   |
| user               | references | null: false |
| content            | string     | null: false |
| nickname           | string     | null: false |
### Association
  belongs_to :room
  belongs_to :user
  has_one_attached :image

