
# テーブル設計

## users テーブル

| Column                        | Type   | Options     |
| ----------------------------- | ------ | ----------- |
| nickname                      | string | null: false |
| email                         | string | null: false |
| password                      | string | null: false |
| encrypted_password            | string | null: false |
| last_name                     | string | null: false |
| first_name                    | string | null: false |
| last_name_kana                | string | null: false |
| first_name_kana               | string | null: false |
| birthday                      | date   | null: false |


### Association

- has_many :items
- has_many :comments
- has_many :buyers

## items テーブル

| Column                          | Type       | Options                        |
| ------------------------------- | ---------- | ------------------------------ |
| title                           | string     |                                |
| price                           | integer    |                                |
| product_condition_id            | integer    |                                |
| postage_id                      | integer    |                                |
| prefecture_id                   | integer    |                                |
| delivery_date_id                | integer    |                                |
| category_id                     | integer    |                                |
| user                            | references | null: false, foreign_key: ture |

### Association

- has_many :comments
- has_one :buyers
- belongs_to :users

## comments テーブル

| Column                  | Type       | Options                        |
| ----------------------- | ---------- | ------------------------------ |
| text                    | text       |                                |
| user                    | references | null: false, foreign_key: ture |
| item                    | references | null: false, foreign_key: ture |

### Association

- belongs_to :items
- belongs_to :users


## buyers テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| user               | references | null: false, foreign_key: ture |
| item               | references | null: false, foreign_key: ture |
| address            | references | null: false, foreign_key: ture |

### Association

- has_one :users
- has_many :items
- has_many :comments
- has_one :addresses

## addresses テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| postcode           | string     | null: false                    |
| prefecture_id      | string     | null: false                    |
| city               | string     | null: false                    |
| block              | string     | null: false                    |
| building           | string     | null: false                    |
| phone_number       | string     | null: false                    |
| buyers             | references | null: false, foreign_key: ture |

### Association

- belongs_to :items
