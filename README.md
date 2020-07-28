# ChatSpace データベースの設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|id|integer|index: true, null: false, unique: true|
|name|string|null: false|
|email|string|null: false|
|password|string|null: false|
### Association
- has_many :groups, through: :groups_users
- has_many :groups_users
- has_many :posts

## postsテーブル
|Column|Type|Options|
|------|----|-------|
|id|integer|index: true, null: false, unique: true|
|image|string||
|text|text||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|id|integer|index: true, null: false, unique: true|
|name|string|null: false|
|user_id|integer|null: false, foreign_key: true|
### Association
- has_many :users, through: :groups_users
- has_many :groups_users
- has_many :posts

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user