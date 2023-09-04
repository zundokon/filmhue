# テーブル設計

## users テーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| nickname           | string | null: false               |

### Association

- has_many :posts
- has_many :favorites
- has_many :views


## posts テーブル
| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| title              | string     | null: false                    |
| review             | text       | null: false                    |
| spoiler            | boolean    | null: false                    | <!--ネタバレ>
| color              | string     |                                | <!--モデルで条件分岐>
| color_code_id      | integer    |                                |
| user               | references | null: false, foreign_key: true |
| location           | string     |                                |
| date               | date       |                                |

### Association

- belongs_to :user
- has_many :favorites
- has_many :views


## favorites テーブル
| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| user               | references | null: false, foreign_key: true |
| post               | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :post


## views テーブル
| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| user               | references | null: false, foreign_key: true |
| post               | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :post