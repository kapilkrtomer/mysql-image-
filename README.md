mysql-image-
============



import MySQLdb
def supermain():
    db = MySQLdb.connect("localhost","root","6Tresxcvbhy")
    cursor = db.cursor()

    sql = """create database IF NOT EXISTS zivame"""
    cursor.execute(sql)

    sql =""" use zivame """
    cursor.execute(sql)    
    #dte TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,

    sql = """create table IF NOT EXISTS  zivame_images (
               task_id int(11) NOT NULL AUTO_INCREMENT,
               product_id varchar(50),
               image_link text,
               PRIMARY KEY (task_id)
	     )"""

    cursor.execute(sql)

    sql = """alter ignore  table  zivame_images add upload_image_status enum('NO','YES', 'F') DEFAULT 'NO';"""

    try:
        cursor.execute(sql)
        db.commit()
    except:
        pass

    sql = """alter ignore  table  zivame_images add failing_status  enum('NO','YES', 'F') DEFAULT 'NO';"""

    try:
        cursor.execute(sql)
        db.commit()
    except:
        pass
  
    db.close()
    print " db_close()......................................................"
if __name__=="__main__":
    supermain()
