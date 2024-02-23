import datetime
import os

class LibraryManagementSystem:
    """This class is used to keep records of book library.
    It has total four modules: "Display books","Issue books","Return books","Add books" """
    def __init__(self, list_of_books, library_name):
        self.sample_file_books = "list_of_book.txt"
        self.library_name = library_name
        self.books_dict = {}
        id = 101
        with open(list_of_books) as bk:
            content = bk.readlines()
            for line in content:
                self.books_dict[str(id)]={'books_title':line.replace("\n",""),'lender_name':'','lend_date':'', 'status':'Available'}
                id += 1

    def display_books(self):
        print("------------------------List of Books---------------------")
        print("Books ID","\t", "Title")
        print("----------------------------------------------------------")
        for key, value in self.books_dict.items():
            print(key,"\t\t", value.get("books_title"), "- [", value.get("status"),"]")

    def issue_books(self):
        books_id = input("Enter Books ID : ")
        current_date = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        if books_id in self.books_dict.keys():
            if not self.books_dict[books_id]['status'] == 'Available':
                print(f"This book is already issued to {self.books_dict[books_id]['lender_name']} on {self.books_dict[books_id]['lend_date']}")
                return
            elif self.books_dict[books_id]['status'] == 'Available':
                your_name = input("Enter Your Name : ")
                self.books_dict[books_id]['lender_name'] = your_name
                self.books_dict[books_id]['lend_date'] = current_date
                self.books_dict[books_id]['status']= 'Already Issued'
                print("Book Issued Successfully !!!\n")
        else:
            print("Book ID Not Found !!!")
            return self.issue_books()

    def add_books(self):
        new_books = input("Enter Books Title : ")
        if new_books == "":
            return self.add_books()
        elif len(new_books) < 20:
            print("Books title length is too long !!! Title length limit is 20 characters")
            return self.add_books()
        else:
            with open(self.sample_file_books, "a") as b:
                b.writelines(f"{new_books}\n")
            self.books_dict.update({str(int(max(self.books_dict))+1):{'books_title':new_books,'lender_name':'','lend_date':'', 'status':'Available'}})
            print(f"The books '{new_books}' has been added successfully !!!")
            return self.add_books()

if __name__ == "__main__":
    try:
        mylms = LibraryManagementSystem("C:\\Users\\USER\\Downloads\\samplefile.txt", "Python's")
        press_key_list = {"D": "Display Books", "I": "Issue Books", "A": "Add Books", "R": "Return Books", "Q": "Quit"}    
        
        key_press = False
        while not (key_press == "q"):
            print(f"\n----------Welcome To {mylms.library_name}'s Library Management System---------\n")
            for key, value in press_key_list.items():
                print("Press", key, "To", value)
            key_press = input("Press Key : ").lower()
            if key_press == "i":
                print("\nCurrent Selection : ISSUE BOOK\n")
                mylms.issue_books()
                
            elif key_press == "a":
                print("\nCurrent Selection : ADD BOOK\n")
                mylms.add_books()

            elif key_press == "d":
                print("\nCurrent Selection : DISPLAY BOOKS\n")
                mylms.display_books()
            
            elif key_press == "r":
                print("\nCurrent Selection : RETURN BOOK\n")
                mylms.return_books()
            elif key_press == "q":
                break
            else:
                continue
    except Exception as e:
        print("An error occurred:", e)
        

I=LibraryManagementSystem("C:\\Users\\USER\\Downloads\\samplefile.txt","Tabitha Library")
I.display_books()

