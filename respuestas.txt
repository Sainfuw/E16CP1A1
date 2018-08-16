CREATE DATABASE call_list;
\c call_list
CREATE TABLE users (id SERIAL PRIMARY KEY ,first_name VARCHAR(20),email VARCHAR(30));
INSERT INTO users (first_name, email) VALUES ('Carlos', 'carlitos@gmail.com');
INSERT INTO users (first_name, email) VALUES('Laura','soylanumero1@gmail.com');
CREATE TABLE calls (id SERIAL PRIMARY KEY, phone INTEGER, date DATE, user_id INTEGER REFERENCES users(id));
ALTER TABLE users ADD COLUMN last_name VARCHAR(30);
UPDATE users SET last_name = 'Rivera' WHERE first_name = 'Carlos';
UPDATE users SET last_name = 'Monsalve' WHERE first_name = 'Laura';
INSERT INTO calls (phone, date, user_id) VALUES (123456, '2018-5-5', 2),(123456, '2018-5-5', 2),(123455, '2018-4-5', 2),(857664, '2018-3-15', 2),(122233455, '2018-4-25', 2),(555555, '2018-1-22', 2);
INSERT INTO calls (phone, date, user_id) VALUES (123456, '2018-7-25', 1),(123455, '2018-8-2', 1), (8787664, '2018-3-5', 1),(7685155, '2018-9-12',1);
INSERT INTO users (first_name, email, last_name) VALUES ('Emilio','sainfuw@gmail.com','Navarro');
SELECT first_name, COUNT(phone) FROM users LEFT JOIN calls ON (users.id = calls.user_id) GROUP BY first_name;
SELECT calls.*  FROM users LEFT JOIN calls ON (users.id = calls.user_id) WHERE first_name = 'Carlos' ORDER BY date DESC;
CREATE TABLE Auditories (reason VARCHAR(100),user_id INTEGER REFERENCES users(id));

https://www.draw.io/?lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&title=Untitled%20Diagram.xml#R7Vxbb9s2GP01flygu%2B3H2Es2YAkWJB3WPhW0RUvEKFGg6Nrurx8pkZZkxrDm6JJkbANE%2FHjnOYcyDxhP3GWy%2F42CLH4kIcQTxwr3E%2FfXieM4nm%2FzXyJyKCOBMysDEUVhGbKrwAv6CWXQktEtCmHeKMgIwQxlzeCapClcs0YMUEp2zWIbgpu9ZiCCWuBlDbAe%2FRuFLJZR27KqjN8himLZ9cyXGSuw%2FieiZJvK%2FiaOuyn%2BldkJUG3J8nkMQrKrhdy7ibukhLDyKdkvIRZrq5atrHd%2FJvc4bgpT1qaC45c1fgC8lXP%2FK4c0l6NjB7Ui%2BQ4lGKQ8tdiQlL3IHIun1zHC4QM4kK3oMmd8CVRqEROKfvLyAPMsmwd4NmUScCcQrSGMlwQTWvTjQkv8b9R8ES3KvijMed0nNT%2F7JPQI9o2CDyBnapQEY5DlaFWMW1RMAI1QuiCMkUQWUrO8bw5KQuguAEZRymNr3hekai3K2die6FZAD0PVnEJXJCIM8vw4mASt5XPMErU4EgtIGdyfBdQ%2B0oTLD5IEMnrgRWSFX1xXUktKzxYJkd7ViBzIMnGNw7bnSQFJ8UTHxisC8QfJoTN8CjQ%2B8SyNTDHIxCOfFkMAP3MJgzQSuQtGMrkuGG4UdlSOUjyvFF52DY%2By7EKsHOIqvpXhBIVh0WqdZCkpWJxnYI3S6KHsxfWq0LPsTYQIb3KDCwxj3hhMC4wZYGB15H9GUMqKNfMX%2FIcv7dK68Sc%2Bn%2BmSp%2B0qzX9EccqWJM0ZBajAFHKS7qAg6iKkJPvCaQnVbOta80%2F45rRlTClynTKHJmaXCKKI9SZ%2BTDV%2BPP3xZn6s6hp%2BBeu2NGlyojNKXEJdTFMSujW%2B8s0n%2B6xeKA3cg9dxrwHt9oXzTMN5g2jOvqcggf3sB9ZloIvGPvhm0LH4%2FZbiV5vEm0gx10gxtvRLRnw23c%2Bu0n0XEKt2axDzjz1G9u9N9rOWHwo74YRtZD%2BE7F3rdciHkL2jQQwTgLCR%2FPuRvG3NBtS8azQ%2FiOad8TTvdQ%2BxkXt3clf4XPR9OjjuubqNaOTeh9y9q%2BTeCcS6s3e7DREjFEFjF39Yuzg4cYvn05a7hj3rgFO6G2jc4rHdYveMaziCW%2BzqLqJxi3t7t0yverd0gXOgHx%2B3OaTf%2B9oM%2Fn%2BfKAd40VzYN4Y0mgP99Hk%2F%2Br7xKT%2BQBuOdPz3dVqR8xiQ1e8aAp9ALqh%2FSZ%2Fb0t4jRfA%2Ba984cKYbQfA8%2Bg1F7Z2pvbTF3YUh4uiFh5N6H3M%2F4jAN4Tp7uD%2FDVxsZu%2Bix2k2e13C%2B6uJvo6W6CcZvGdpu8M67DCG6Tp19PMm5Tb2%2BV6%2B4odYGzr%2B8Dxm36aG7ThX1jSLfJ1%2FcN4zb1smn4411s9HVzIYsFEmbLGO74eUH0Q5pNvrngNIzkxzOYff2CUwiYUfw7Uvygdxp9c8lpGMlfd8mpE4h78BSN3LuT%2B5B3Gn3dfDRy70Pu1%2F2VYhcQBy3kDsMIKpeLjxmxwzPEgCGS3lU52orUjrMwDW%2FFVxLw5N0zh%2FkLeQTpYSLN5iorAWn4Z8ECuEfsq6h9Y1mBTH8TmN04wbRokc%2FzqwSxSJS5viz7BCniayEs4KJIOScxkbPCk6GcbOkaNvdTplTd7gB2%2FI6EJlgySIu1%2B9EcyGsQyj6eBEVr%2FrF9%2Btft85Ndv5yBrFYxQW9p2mxofkKnctZaOwWjjhNvRzLdbnoXJLtAIklA220QcNY7xVrcKOmZYvMmM1zl7%2FxnijnWSUuzrkjGk9V3hJTFqy9ice%2F%2BBQ%3D%3D
