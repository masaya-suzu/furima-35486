
# テーブル設計

## users テーブル

| Column                      | Type   | Options     |
| --------------------------- | ------ | ----------- |
| nickname                    | string | null: false |
| email                       | string | null: false |
| password                    | string | null: false |
| confirm_password            | string | null: false |
| last_name                   | string | null: false |
| first_name                  | string | null: false |
| last_name_kana              | string | null: false |
| first_name_kana             | string | null: false |
| birthday                    | date   | null: false |


### Association

- has_many :items
- has_many :comments
- has_many :buyers

## items テーブル

| Column                       | Type       | Options                        |
| ---------------------------- | ---------- | ------------------------------ |
| title                        | string     |                                |
| price                        | integer    |                                |
| product_condition            | text       |                                |
| postage                      | text       |                                |
| delivery_source              | text       |                                |
| delivery_date                | text       |                                |
| user                         | references | null: false, foreign_key: ture |

### Association

- has_many :comments
- has_many :buyers
- belongs_to :users

## comments テーブル

| Column                  | Type       | Options                        |
| ----------------------- | ---------- | ------------------------------ |
| text                    | text       |                                |
| user                    | references | null: false, foreign_key: ture |
| item                    | references | null: false, foreign_key: ture |

### Association

- belongs_to :comments
- belongs_to :users


## buyers テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| credit             | string     |                                |
| user               | references | null: false, foreign_key: ture |
| item               | references | null: false, foreign_key: ture |
| address            | references | null: false, foreign_key: ture |

### Association

- has_many :buyers
- has_many :comments
- has_many :addresses

## addresses テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| postcode           | string     |                                |
| prefecture_id      | string     |                                |
| city               | string     |                                |
| block              | string     |                                |
| building           | string     |                                |
| phone_number       | integer    |                                |

### Association

- has_many :buyers
