
# テーブル設計

## users テーブル

| Column                        | Type   | Options                   |
| ----------------------------- | ------ | ------------------------- |
| nickname                      | string | null: false               |
| email                         | string | null: false, unique: true |
| password                      | string | null: false               |
| encrypted_password            | string | null: false               |
| last_name                     | string | null: false               |
| first_name                    | string | null: false               |
| last_name_kana                | string | null: false               |
| first_name_kana               | string | null: false               |
| birthday                      | date   | null: false               |


### Association

- has_many :items
- has_many :buyers

## items テーブル

| Column                          | Type       | Options                        |
| ------------------------------- | ---------- | ------------------------------ |
| title                           | string     | null: false                    |
| price                           | integer    | null: false                    |
| product_condition_id            | integer    | null: false                    |
| postage_id                      | integer    | null: false                    |
| prefecture_id                   | integer    | null: false                    |
| delivery_date_id                | integer    | null: false                    |
| category_id                     | integer    | null: false                    |
| item_info                       | integer    | null: false                    |
| user                            | references | null: false, foreign_key: ture |

### Association

- belongs_to :user

## comments テーブル

| Column                  | Type       | Options                        |
| ----------------------- | ---------- | ------------------------------ |
| text                    | text       |                                |
| user                    | references | null: false, foreign_key: ture |
| item                    | references | null: false, foreign_key: ture |

### Association

- belongs_to :item
- belongs_to :user


## buyers テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| user               | references | null: false, foreign_key: ture |
| item               | references | null: false, foreign_key: ture |
| address            | references | null: false, foreign_key: ture |

### Association

- belongs_to :user
- belongs_to :item
- has_one :address

## addresses テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| postcode           | string     | null: false                    |
| prefecture_id      | integer    | null: false                    |
| city               | string     | null: false                    |
| block              | string     | null: false                    |
| building           | string     |                                |
| phone_number       | string     | null: false                    |
| buyers             | references | null: false, foreign_key: ture |

### Association

- belongs_to :buyer
