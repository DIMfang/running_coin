# Running Coin Database Desgin

## Table#1 User_Group

| GroupId               | GroupName    | MetaData      |
| --------------------- | ------------ | ------------- |
| int(16)               | varchar(256) | varchar(2000) |
| Primary Key(Sequence) | Unique       |               |

## Table#2 User_Info

| UserId                | GroupId     | UserName     | Status          | Role         | Coins      | Icon | TotalDistance | MetaData      |
| --------------------- | ----------- | ------------ | --------------- | ------------ | ---------- | ---- | ------------- | ------------- |
| int(16)               | int(16)     | varchar(256) | varchar(32)     | varchar(32)  | int(16)    | blob | float(9,1)    | varchar(2000) |
| Primary Key(Sequence) | Foreign Key |              | Active/Inactive | Admin/Member | Default  0 |      |               |               |

## Table#3 Running_Record

| RuningRecordId        | UserId      | Distance   | CreationTime | LastVotedTime | Status                            | Score  | SettledTime | EarnedCoins | Comments     | Evidence |
| --------------------- | ----------- | ---------- | ------------ | ------------- | --------------------------------- | ------ | ----------- | ----------- | ------------ | -------- |
| int(16)               | int(16)     | float(3,1) | TIMESTAMP    | TIMESTAMP     | varchar(32)                       | int(4) | TIMESTAMP   | int(16)     | varchar(256) | blob     |
| Primary Key(Sequence) | Foreign Key |            |              |               | Submitted/Expired/Rejected/Passed |        |             |             |              |          |

## Table#4 Vote_Record

| VoteRecordId          | VoteUserId  | RuningRecordId | VotedTime | CanceledTime | Status         | Score  | Comments    |
| --------------------- | ----------- | -------------- | --------- | ------------ | -------------- | ------ | ----------- |
| int(16)               | int(16)     | int(16)        | TIMESTAMP | TIMESTAMP    | varchar(32)    | int(4) | varchar(32) |
| Primary Key(Sequence) | Foreign Key | Foreign Key    |           |              | Voted/Canceled | 1 / -1 |             |
