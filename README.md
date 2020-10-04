// TopStreamingArtist class

public class TopStreamingArtist {

    private Artist first;

    private Artist last;

    // inner class Artist

    class Artist {

        // data fields

        private String name;

        private Artist next;

        // constructor for Artist class

        public Artist(String name) {

            this.name = name;

            this.next = null;

        }

    }

    // constructor for TopStreamingArtist class

    public TopStreamingArtist() {

        // initialising first and last to null

        first = null;

        last = null;

    }

    // isEmpty method

    public boolean isEmpty() {

        return (first == null);

    }

    // insert method

    void insert(String name) {

        // creating new artist object

        Artist newArtist = new Artist(name);

        if (this.isEmpty()) {

            // if this list is empty

            // setting first and last to newArtist

            first = newArtist;

            last = newArtist;

        } else {

            // otherwise setting last.next to newArtist

            last.next = newArtist;

            // last to newArtist

            last = newArtist;

        }

    }

    // sortList ...to sort names

    public void sortList() {

        // initialising current and index

        Artist current = first, index = null;

        String temp; // to store temporary name

        if (this.isEmpty()) {

            // if empty return

            return;

        } else {

            // otherwise

            while (current != null) {

                // setting index to current -> next

                index = current.next;

                while (index != null) {

                    // if current ->name is alphabetically higher then index->name the swap them

                    if (current.name.compareTo(index.name) > 0) {

                        temp = current.name;

                        current.name = index.name;

                        index.name = temp;

                    }

                    index = index.next; // increment index

                }

                current = current.next; // increment current

            }

        }

    }

    // displayNames() method

    public void displayNames() {

        // setting current to first

        Artist current = first;

        this.sortList(); // calling sortList to sort it

        if (this.isEmpty()) {

            // if empty print message and return

            System.out.println("List is empty");

            return;

        }

        while (current != null) {

            // other while current is not null

            // print the names

            System.out.println(current.name);

            current = current.next; // inrement current

        }

    }

    public static void main(String[] args) {

        // creating object of TopStreamingArtist class

        TopStreamingArtist artistNames = new TopStreamingArtist();

        // adding some names

        artistNames.insert("Stage Name");

        artistNames.insert("Lady Gaga");

        artistNames.insert("Nick Johns");

        artistNames.insert("Taylor Swift");

        artistNames.insert("Justin Bieber");

        artistNames.insert("Chris Brown");

        artistNames.insert("Bruno Mars");

        artistNames.insert("Adele");

        artistNames.insert("Beyonce");

        // calling displauyNames ot print them

        artistNames.displayNames();

    }

}
