Query-1(Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia)

<!-- QUERY -->
SELECT * FROM `students` JOIN `degrees` ON `students`.`degree_id`=`degrees`.`id`
WHERE `degrees`.`name`="Corso di Laurea in Economia";

Query-2(Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze)
RISPOSTA(1)
<!-- QUERY -->
SELECT * FROM `departments` JOIN `degrees` ON `departments`. `id`= `degrees`. `department_id` WHERE `degrees`. `level`="magistrale" AND `departments`.`name`="Dipartimento di Neuroscienze"

Query-3(Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44))
<!-- QUERY -->
SELECT * FROM `teachers`JOIN `course_teacher` ON `course_teacher`.`teacher_id`=`teachers`.`id`
JOIN `courses` ON `course_teacher`.`course_id`=`courses`.`id`
WHERE `teachers`.`id`=44;

Query-4(Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il
relativo dipartimento, in ordine alfabetico per cognome e nome
)


Query-5(Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti)
<!-- QUERY -->
SELECT *
FROM `degrees`
JOIN `courses` ON `degrees`.`id`= `courses`.`degree_id`
JOIN `course_teacher` ON `courses`.`id`=`course_teacher`.`course_id`
JOIN `teachers` ON `course_teacher`.`course_id`=`teachers`.`id`

Query-6(Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
<!-- QUERY -->
SELECT *
FROM `teachers`
JOIN `course_teacher` ON `teachers`.`id`=`course_teacher`.`teacher_id`
JOIN `courses` ON `course_teacher`.`course_id`=`courses`.`id`
JOIN `degrees` ON `courses`.`degree_id`=`degrees`.`id`
JOIN `departments` ON `degrees`.`department_id`=`departments`.`id`
WHERE `departments`.`name`="Dipartimento di Matematica";

Query-7 (BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami)
<!-- QUERY -->
SELECT `students`.`id`, `students`.`name`, `students`.`surname`, `courses`.`name`, COUNT(`exam_student`.`vote`)
AS "numero_tentaivi", MAX(`exam_student`.`vote`) AS "voto_massimo"
FROM `students`
JOIN `exam_student` ON `students`.`id`= `exam_student`.`student_id`
JOIN `exams` ON `exam_student`.`exam_id`=`exams`.`id`
JOIN `courses` ON `exams`.`course_id`=`courses`.`id`
GROUP BY `students`.`id`, `courses`.`id`
HAVING(`voto_massimo` >18);