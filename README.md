## DB設計

### usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false,unique: true|
|email|string|null: false,unique: true|

#### Association
- has_many :groups, through: :members
- has_many :messages
- has_many :menbers

### groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

#### Association
- has_many :users, through: :members
- has_many :messages
- has_many :members

### messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text||
|image|text||
|user_id|reference|null: false, oreign_key: true|
|group_id|reference|null: false, oreign_key: true|

#### Association
- belongs_to :user
- belongs_to :group


### membersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|reference|null: false, oreign_key: true|
|group_id|reference|null: false, oreign_key: true|

#### Association
- belongs_to :user
- belongs_to :group
