### Mechanism: Expand and contract

1. Expand: Adding new fields
2. Backfill: Fill the data from old field to the new field
3. Dual writes: When having the new data to new rows, add data to both 2 fields old and new ones
4. Read switch: Reading on the new data after having all of new data
5. Contract: After it's stable for a long time, do cleaning up old fields, old data. 

### Before production
1. Test logic with new schema
2. Run migrate on staging to check `table locking` issue to check there're no impacts to the main application logic
3. Backup / Restore data plan. 