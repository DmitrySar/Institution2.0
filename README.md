# Информационная система учебного заведения
## Диаграмма классов
![Картинка](https://sun1-92.userapi.com/Ss12lACg9j_NFb4BJp-NfuhYF6j17d1Hm2Hi5g/DHsVQzDjrKA.jpg)
## Пример исполняемого класса
```Java
class Main {
  public static void main(String[] args) throws IOException {
    Institution institution = new Institution("ВУЗ", "г. Город");
    
    Files.readAllLines(Paths.get("res/students.txt"), UTF_8)
      .forEach(s -> institution.addStudent(new Student(s)));
      
    Files.readAllLines(Paths.get("res/lecturers.txt"), UTF_8)
      .forEach(l -> institution.addLecturer(new Lecturer(l)));
      
    Files.readAllLines(Paths.get("res/courses.txt"), UTF_8)
      .forEach(c -> institution.addCourse(new Course(c)));
      
      System.out.println("\nсписок студентов:");
      institution.getStudents().forEach(System.out::println);
      System.out.println("\nсписок преподавателей:");
      institution.getLecturers().forEach(System.out::println);
      System.out.println("\nсписок предметов:");
      institution.getCourses().forEach(System.out::println);
      
      institution.getStudents().forEach(s -> institution.studentForCourseAssociate(s, institution.getCourse(11)));
      
      System.out.println("\nКол-во студентов, изучающих курс физики: ");
      System.out.println(institution.getCourse(11).getStudents().size());
  }
}
```
[Выполнить](https://Institution20.dmitrysar.repl.run)
