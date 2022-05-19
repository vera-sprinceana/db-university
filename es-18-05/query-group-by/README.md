
Query-1
(Contare quanti iscritti ci sono stati ogni anno)
RISULTATO:
iscritti_ogni_anno
912 NEL 2018
1709 NEL 2019
1645 NEL 2020
734 NEL 2021
<!-- QUERY -->
SELECT COUNT(`enrolment_date`) AS `iscritti_ogni_anno`, YEAR(`enrolment_date`)
FROM `students` 
GROUP BY YEAR(`enrolment_date`);

Query-2 (Contare gli insegnanti che hanno l'ufficio nello stesso edificio)
RISPOSTA (29)
<!-- QUERY -->
SELECT COUNT(`id`) AS `stesso_indirizzo`, (`office_address`)
FROM `teachers`
GROUP BY `office_address`;

Query-3 (Calcolare la media dei voti di ogni appello d'esame)
RISPOSTA (17.9573)
<!-- QUERY -->
SELECT AVG(`vote`) AS `media_voti` FROM `exam_student` GROUP BY `exam_id`;

Query-4(Contare quanti corsi di laurea ci sono per ogni dipartimento)
RISPOSTA(75)
<!-- QUERY -->
SELECT COUNT(`id`) AS `corsi_per_dipartimento` FROM `courses` GROUP BY `degree_id`
SELECT COUNT(*) `department_id` FROM `degrees` GROUP BY `department_id`;