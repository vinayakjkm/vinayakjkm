SELECT AVG(grade) AS average_grade
FROM Enrollments;
SELECT s.name AS student_name, c.course_name
FROM Students s
JOIN Enrollments e ON s.student_id = e.student_id
JOIN Courses c ON e.course_id = c.course_id;
SELECT grade_level, COUNT(*) AS student_count
FROM Students
GROUP BY grade_level;
SELECT c.course_name, MAX(e.grade) AS max_grade
FROM Courses c
JOIN Enrollments e ON c.course_id = e.course_id
GROUP BY c.course_name;
SELECT AVG(e.grade) AS average_grade
FROM Enrollments e
JOIN Students s ON e.student_id = s.student_id
WHERE s.grade_level = 3;
SELECT s.name AS student_name, c.course_name, c.credits
FROM Students s
JOIN Enrollments e ON s.student_id = e.student_id
JOIN Courses c ON e.course_id = c.course_id;
SELECT c.course_name
FROM Courses c
JOIN Enrollments e ON c.course_id = e.course_id
GROUP BY c.course_name
HAVING AVG(e.grade) > 3.0;
SELECT DISTINCT s.name
FROM Students s
WHERE s.student_id NOT IN (
    SELECT e.student_id
    FROM Enrollments e
    WHERE e.grade = 4.0
);
SELECT s.name
FROM Students s
JOIN Enrollments e ON s.student_id = e.student_id
GROUP BY s.student_id
HAVING AVG(e.grade) > (SELECT AVG(grade) FROM Enrollments);
SELECT s.name AS student_name, 
       COUNT(e.course_id) AS total_courses, 
       AVG(e.grade) AS average_grade
FROM Students s
LEFT JOIN Enrollments e ON s.student_id = e.student_id
GROUP BY s.student_id;

