# DB設計

## users table
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false,  unique: true|
### Association
- has_many :groups, through:groups_users
- has_many :group_users
- has_many :messages

## groups table
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :users, through:groups_users
- has_many :group_users
- has_many :messages

## messages table
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|text||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user


## groups_users table //中間テーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user
