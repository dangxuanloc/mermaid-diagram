erDiagram

  demo-customers {
    INT id
    VARCHAR name
    VARCHAR email
  }

  demo-orders {
    INT id
    INT customer_id
    DATE order_date
    DECIMAL total_amount
  }

  demo-customers ||--o{ demo-orders : "foreign key"
