---
layout: post
title: Eliminating boilerplate code with aspects and templates
permalink: /:collection/spring/aop/eliminate-bolierplate-with-aspects
---

- **Boilerplate code** - code write over and over again to accomplish common and otherwise simple tasks.
- JDBC, JMS, JNDI, consumption of REST services.
- Spring eliminate boilerplate code by encapsulating it in templates.

**JDBC Template**
```java
public Employee getEmployeeById(long id) {
    String query = "select id, firstname, lastname, salary " + "from employee where id=?";
    RowMapper<Employee> rowMapper = new RowMapper<Employee>() {
        public Employee mapRow(ResultSet rs, int rowNum) throws SQLException {
            Employee employee = new Employee();
            employee.setId(rs.getLong("id"));
            employee.setFirstName(rs.getString("firstname"));
            employee.setLastName(rs.getString("lastname"));
            employee.setSalary(rs.getBigDecimal("salary"));
            return employee;
        }
    }
    return jdbcTemplate.queryForObject(query, RowMapper, id);
}
```

The template’s queryForObject() method is given the SQL query, a RowMapper (for mapping result set data to a domain object), and zero or more query parameters. What you don’t see in getEmployeeById() is any of the JDBC boilerplate from before. Everything is handled inside the template.

But how do those files get loaded? And what are they loaded into? Let’s look at the Spring container, the place where your application’s beans reside.

```java
@AfterReturning(pointcut="args(name)", returning="returningString")
public void returnStringforStringArgsMethod(String name, String returningString){...}

@AfterThrowing(pointcut="args(name)", throwing="ex")
public void returnStringforStringArgsMethod(String name, Exception ex){...}
```

**Normal JDBC Code**
```java
public Employee getEmployeeById(long id) {
    Connection conn = null;
    PreparedStatement stmt = null;
    ResultSet rs = null;
    try {
        conn = dataSource.getConnection();
        stmt = conn.prepareStatement("select id,firstname,
            lastname, salary from "+"
            employee where id = ? ");
            stmt.setLong(1, id);
            rs = stmt.executeQuery();
            Employee emp = null;
            if(rs.next()) {
                emp = new Employee();
                emp.setId(rs.getLong("id"));
                emp.setFirstName(rs.getString("firstname"));
                emp.setLastName(rs.getString("lastname"));
                emp.setSalary(rs.getBigDecimal("salary"));
            }
            return employee;
        }
        catch (SQLException e) {
            Sysout(e);
        } finally {
            if (rs != null) {
                try {
                    rs.close();
                } catch (SQLException e) {}
            }
            if (stmt != null) {
                try {
                    stmt.close();
                } catch (SQLException e) {}
            }
            if (conn != null) {
                try {
                    conn.close();
                } catch (SQLException e) {}
            }
        }
        return null;
    }
}
```
