class DoesNotExist(Exception):
    pass
class MultipleObjectsReturned(Exception):
    pass
class InvalidField(Exception):
    pass

class Student:
    def __init__(self,name,age,score):
        self.name = name
        self.age = age
        self.score = score 
        self.student_id = None
    
    @staticmethod
    def get(**kwargs):
        for key, value in kwargs.items():
            if key in ['student_id','age', 'score']:
                q = 'SELECT * FROM Student WHERE {} = {}'.format(key,value)
            elif key  == 'name':
                q = 'SELECT * FROM student where {} = \'{}\' '.format(key,value);
            else:
                raise InvalidField
        query = read_data(q)    
        if len(query) == 0:
            raise DoesNotExist
        elif len(query)>1:
            raise MultipleObjectsReturned
        else:
            s = Student(query[0][1], query[0][2],query[0][3])
            s.student_id = query[0][0]
            return s
    
    def delete(self):
        q = 'DELETE FROM Student WHERE student_id = {}'.format(self.student_id);
        write_data(q)   
        
    
    def save(self):
        import sqlite3
        conn = sqlite3.connect("students.sqlite3")
        crsr = conn.cursor()
        crsr.execute("PRAGMA foreign_keys= on;")
        if self.student_id == None:
            q = 'INSERT INTO Student(student_id,name,age,score) VALUES(Null,\'{}\', {},{})'.format(self.name,self.age,self.score);
            crsr.execute(q) 
            self.student_id = crsr.lastrowid
            
        elif self.name != None:
            q = 'INSERT or REPLACE INTO Student(student_id,name,age,score) VALUES({},\'{}\', {},{})'.format(self.student_id,self.name,self.age,self.score);
            crsr.execute(q) 
            
        # else:

        #     q = "UPDATE student SET name = \'{}\' ,age = {}, score = {} where student_id ={}".format(self.name, self.age,self.score,self.student_id);
        #     crsr.execute(q)     
        conn.commit()
        conn.close()
    

    
   
def write_data(sql_query):
	import sqlite3
	connection = sqlite3.connect("students.sqlite3")
	crsr = connection.cursor() 
	crsr.execute("PRAGMA foreign_keys=on;")  
	crsr.execute(sql_query) 
	connection.commit() 
	connection.close()

def read_data(sql_query):
	import sqlite3
	connection = sqlite3.connect("students.sqlite3")
	crsr = connection.cursor() 
	crsr.execute(sql_query) 
	ans= crsr.fetchall()  
	connection.close() 
	return ans


'''
 @staticmethod   
    def get(student_id = None,name = None,age = 0,score = -1):
        if student_id != None:
            q = 'SELECT * FROM Student WHERE student_id = {}'.format(student_id);
        elif name != None:
            q = 'SELECT * FROM Student WHERE name = \'{}\' '.format(name);
        elif age != 0:
            q = 'SELECT * FROM Student WHERE age = {}'.format(age);
        elif score != -1:
            q = 'SELECT * FROM Student WHERE score = {}'.format(score);
        else:
            raise InvalidField

        result = read_data(q)
        if len(result)>1:      
            raise MultipleObjectsReturned
        elif len(result) ==0:
            raise DoesNotExist
            
        else:
            s = Student(result[0][1],result[0][2],result[0][3])
            s.student_id = result[0][0]
            return s 
     
'''   
            

