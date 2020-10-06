public class TopStreamingArtists {
    Aritist head = null;

    static class Aritist {
        public String name;
        public Aritist next;

        public Aritist(String name) {
            this.name = name;
            this.next = null;
        }
    }

    public static void main(String[] args) throws IOException {
        TopStreamingArtists list = new TopStreamingArtists();
        //use this String array or read from text file
        String[] a1 = {"abc", "w", "ab", "z","b"};
        for(String s: a1)
            list.add(s);
        list.display();
        /**************************************************
         *************************************************/
        //Reading from text file
        File file = new File("C:\\Users\\rohith\\Desktop\\test.txt");
        BufferedReader br = new BufferedReader(new FileReader(file));
        String st;
        while ((st = br.readLine()) != null) {
                list.add(s);
        }
        list.display();
    }

    /**
     *
     * @param name Adds the name in appropriate position in the list
     */
    public void add(String name) {
        Aritist curr = head;
        if (curr == null) {
            head = new Aritist(name);
            return;
        }
        if(name.compareTo(head.name) < 0) {
            Aritist n = new Aritist(name);
            n.next = head;
            head = n;
            return;
        }
        Aritist prev = null;
        while (curr != null && curr.name.compareTo(name) < 0) {
            prev = curr;
            curr = curr.next;

        }
        if (curr != null) {
            Aritist temp = curr;
            prev.next = new Aritist(name);
            prev.next.next = temp;
        }
        else {
            prev.next = new Aritist(name);
        }
    }

    /**
     * Prints the numbers in list
     */
    public void display() {
        Aritist curr = head;
        while (curr != null) {
            System.out.println(curr.name + " ");
            curr = curr.next;
        }
    }
