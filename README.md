# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

## messagesテーブル
|Column|Type|Option|
|------|----|------|
|body|text|null: false|
|image|string||
|group_id|integer|null: false|
|user_id|integer|null: false|
### Association
- belongs_to :user
- has_many :groups

## usersテーブル
|Column|Type|Option|
|------|----|------|
|name|string|null: false, unique: true|
|email|string|null: false, unique: true|
|password|string|null: false|
### Association
- has_many :messages
- has_many :groups, through: groups_users

## groupsテーブル
|Column|Type|Option|
|------|----|------|
|group_name|string|null: false|
|user_id|integer|null: false|
|message_id|integer|null: false|
### Association
has_many :users, through: groups_users
has_many :messages

## groups_usersテーブル
|Column|Type|Option|
|------|----|------|
|user_id|integer|null: false|
|group_id|integer|null:false|
