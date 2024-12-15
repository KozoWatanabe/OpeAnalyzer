# README

## rooms テーブル


|Column	             | Type	        | Options             |
|--------------------|--------------|---------------------|
|name                | string	      | null: false         |

### Association
- has_many :operations
- has_many :staffs, through: :operations

## staffs テーブル

|Column	             | Type	        | Options             |
|--------------------|--------------|---------------------|
|name                |  string      | null: false         |
|role_id             |  integer     | null: false         |

### Association
- has_many :operation_staffs
- has_many :operations, through: :operation_staffs

## operations テーブル

|Column	              | Type	       |Options                  |
|---------------------|--------------|-------------------------|
|department	          | string	     | null: false             |
|entry_time           |	datetime     | null: false             |
|exit_time            |	datetime     | null: false             |
|operation_start_time | datetime     | null: false             |
|operation_end_time   |	datetime     | null: false             |
|anesthesia_start_time| datetime     | null: false             |
|anesthesia_end_time  | datetime     | null: false             |
|room_id              | references   | null: false, foreign_key: true |
|operation_date       | date         | null: false             |


### Association
- belongs_to :room
- has_many :operation_staffs
- has_many :staffs, through: :operation_staffs


## operation_staffs テーブル

|Column	          | Type              |	Options                        |
|-----------------|-------------------|--------------------------------|
|operation_id   	| references	      | null: false, foreign_key: true |
|staff_id	        | references	      | null: false, foreign_key: true |

## Association:
- belongs_to :operation
- belongs_to :staff