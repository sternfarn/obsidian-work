
```base
filters:
  and:
    - file.inFolder("")
views:
  - type: calendar
    name: Calendar
    order:
      - file.name
      - file.tags
      - done
      - text
      - list
    startDate: note.date
    endDate: note.deadline
  - type: cards
    name: Cards

```

