# README

# テーブル設計

## users テーブル
| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| nickname           | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |

### Association
- has_many :tweets
- has_many :comments


## tweets テーブル
| Column               | Type       | Options           |
| -------------------- | ---------- | ------------------|
| text                 | text       | null: false       |


### Association
- has_many :comments
- has_many :tweets_tags


## comments テーブル
| Column  | Type       | Options           |
| ------- | ---------- | ------------------| 
| text    | text       | null: false       |   
| user    | references | foreign_key: true |
| tweet   | references | foreign_key: true |

### Association
- belongs_to :user
- belongs_to :tweet


# tweets_tags テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| tweet  | references | null: false, foreign_key: true |
| tag    | references | null: false, foreign_key: true |

### Association
- belongs_to :tweet
- belongs_to :tag

## tags テーブル
| Column        | Type       | Options           |
| ------------- | ---------- | ----------------- |
| text          | text       | null: false       |   

### Association
- has_many :tweets_tags