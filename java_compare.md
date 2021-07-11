# comparable, compareTo
## code
```java
import java.util.*;

public class main {
	
	private static class Person implements Comparable<Person> {
		String name;
		int id;
		int age;
		int score;
		Person (){}
		Person (String name, int id, int age, int score){
			this.name = name;
			this.id = id;
			this.age = age;
			this.score = score;
		}
		
		public int compareTo(Person p) {
			if(this.score == p.score) {
				return (this.age - p.age) * -1;
			}
			
			return  (this.score - p.score) * -1;
		}
		
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Person[] person = new Person[10];
		person[0] = new Person("kongjunwon", 1, 40, 100);
		person[1] = new Person("leehyoree", 2, 42, 49);
		person[2] = new Person("seojihye", 3, 38, 98);
		person[3] = new Person("limnayeon", 4, 27, 94);
		person[4] = new Person("chojungsuk", 5, 42, 12);
		person[5] = new Person("kominsee", 6, 27, 77);
		person[6] = new Person("kimtaero", 7, 32, 98);
		person[7] = new Person("sondambee", 8, 39, 94);
		person[8] = new Person("jeonmido", 9, 40, 100);
		person[9] = new Person("jeonsomin", 10, 38, 49);
		
		Arrays.sort(person);
		
		LinkedList<Person> plink = new LinkedList<Person>();
		plink.add(new Person("kongjunwon", 1, 40, 100));
		plink.add(new Person("leehyoree", 2, 42, 49));
		plink.add(new Person("seojihye", 3, 38, 98));
		plink.add(new Person("limnayeon", 4, 27, 94));
		plink.add(new Person("chojungsuk", 5, 42, 12));
		plink.add(new Person("kominsee", 6, 27, 77));
		plink.add(new Person("kimtaero", 7, 32, 98));
		plink.add(new Person("sondambee", 8, 39, 94));
		plink.add(new Person("jeonmido", 9, 40, 100));
		plink.add(new Person("jeonsomin", 10, 38, 49));
		
		Collections.sort(plink);
		
		
		System.out.println("aaaaaa");
	}
}

```
## reference
- https://st-lab.tistory.com/243