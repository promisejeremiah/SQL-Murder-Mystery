# SQL-Murder-Mystery
![image](https://github.com/promisejeremiah/SQL-Murder-Mystery/assets/48945500/79deb682-0f3a-4822-90f0-aae63bfb053b)

I took part in the The SQL Murder Mystery which is designed to be both a self-directed lesson to learn SQL concepts and commands and a fun game for experienced SQL users to solve an intriguing crime.

A crime has taken place and the detective needs your help. The detective gave you the crime scene report, but you somehow lost it. You vaguely remember that the crime was a ​murder​ that occurred sometime on ​Jan.15, 2018​ and that it took place in ​SQL City​. Start by retrieving the corresponding crime scene report from the police department’s database.

```
SELECT *
FROM crime_scene_report
WHERE date = 20180115 AND city = 'SQL City';
```

![image](https://github.com/promisejeremiah/SQL-Murder-Mystery/assets/48945500/8cc64d13-e977-4615-b0e3-d93c55e099f1)

Two witnesses were found after retrieving the corresponding crime scene report from the police department’s database.

Now it’s time to dig deep into the witnesses to know what they have to say about the crime.

&nbsp;
&nbsp;

### FIRST WITNESS

```SELECT *
FROM person p
JOIN interview i
ON i.person_id = p.id
WHERE address_street_name LIKE '%Northwestern Dr%'
ORDER BY address_number DESC
LIMIT 1;
```

![image](https://github.com/promisejeremiah/SQL-Murder-Mystery/assets/48945500/afc25331-ab1a-41c4-b244-822cd7edc2e9)


This is the interview from the first witness about the crime.

&nbsp;
&nbsp;

### SECOND WITNESS

```
SELECT *
FROM person p
JOIN interview i
ON i.person_id = p.id
WHERE name LIKE '%Annabel%' AND address_street_name LIKE '%Franklin Ave%';
```

![image](https://github.com/promisejeremiah/SQL-Murder-Mystery/assets/48945500/139c8852-9500-442a-8392-c75298d04f53)

This is the interview from the second witness about the crime.

From the both witnesses it can been seen that the First Witness gave more details about the murderer.

Now it’s time to find the murderer by looking at informations provided by the first witness.

&nbsp;
&nbsp;

```
SELECT *
FROM get_fit_now_member g
JOIN person p
ON g.person_id = p.id
JOIN drivers_license d
ON p.license_id = d.id
WHERE g.id LIKE '48Z%' AND d.plate_number LIKE '%H42W%';
```

![image](https://github.com/promisejeremiah/SQL-Murder-Mystery/assets/48945500/0fee29c4-b160-4a91-adad-7465f7d5d5c5)


After using the informations provided by the second witness we found a name “Jeremy Bowers” we think might be the name of the murderer.

We are going to check the name “Jeremy Bowers” on the solution section to see if he is the murderer.

![image](https://github.com/promisejeremiah/SQL-Murder-Mystery/assets/48945500/4c5cbb59-c6bb-4001-a683-3148eced4e9d)


We can see that the name of the murder who committed the crime is “Jeremy Bowers”.

Now it time to find out who is the real villain behind this crime.

&nbsp;
&nbsp;

```
SELECT *
FROM get_fit_now_member g
JOIN person p
ON g.person_id = p.id
JOIN drivers_license d
ON p.license_id = d.id
JOIN interview i
ON i.person_id = p.id
WHERE g.id LIKE '48Z%' AND d.plate_number LIKE '%H42W%';
```

![image](https://github.com/promisejeremiah/SQL-Murder-Mystery/assets/48945500/cc567239-1fc0-41e2-8500-16d91747e6cc)


It can be see that the murderer “Jeremy Bowers” was hired by someone else to commit the crime.

We are going to dig in deep to find the name of the woman who hired “Jeremy Bowers” to commit the murderer.

&nbsp;
&nbsp;

```
SELECT *
FROM drivers_license d
JOIN person p
ON p.license_id = d.id
JOIN facebook_event_checkin f
ON f.person_id = p.id
WHERE height BETWEEN 65 AND 67
GROUP BY height
HAVING hair_color = 'red' AND car_make = 'Tesla';
```

![image](https://github.com/promisejeremiah/SQL-Murder-Mystery/assets/48945500/d3768e4e-22bb-4eb0-b412-5d54bd7026ea)


Now we have found the name of the woman who we think hired “Jeremy Bowers” to commit the murderer. We are going to check the name of the woman on the solution section.

![image](https://github.com/promisejeremiah/SQL-Murder-Mystery/assets/48945500/fa941593-de93-4b79-9b07-13d05bccb2fb)


“Miranda Priestly” is the woman who hired “Jeremy Bowers” to commit the murderer.

She is the brain behind the murder.
