## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false, unique: true|
|encrypted_password|string|null: false|
|image|string||
|comment|text||

### Association
- has_many :recipes
- has_many :reports
- has_many :likes
- has_many :myrecipes

## recipesテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|image|string|null: false|
|comment|text||
|time|string|null: false|
|amount|string|null: false|
|point|text||
|background|text||
|user_id|references|null: false, foreign_key: true|

### Association
- has_many :processes
- has_many :foods
- has_many :reports
- has_many :myrecipes
- has_many :likes
- belongs_to :user

## processesテーブル

|Column|Type|Options|
|------|----|-------|
|image|string||
|process|text||
|recipe_id|references|null: false, foreign_key: true|

### Association
- belongs_to :recipe

## foodsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|amount|string|null: false|
|recipe_id|references|null: false, foreign_key: true|

### Association
- belongs_to :recipe

## reportsテーブル

|Column|Type|Options|
|------|----|-------|
|image|string|null: false|
|comment|text|null: false|
|recipe_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :recipe
- belongs_to :user

## myrecipesテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|recipe_id|references|null: false, foreign_key: true|

### Association
- belongs_to :recipe
- belongs_to :user

## likesテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|recipe_id|references|null: false, foreign_key: true|

### Association
- belongs_to :recipe
- belongs_to :user