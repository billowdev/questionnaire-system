```sql
// Use DBML to define your database structure
// Docs: https://dbml.dbdiagram.io/docs

Table User [note: "ตารางผูใช้"] {
	  id uuid [pk, not null, note: "The pk filed for user"]
		username string [not null, note:"The username field for user to login"]
		password string [not null, note:"รหัสผ่าน"]
		email string
		status string 
}

Table SupervisionFormType {
  id uuid(36)
  type string(255)
  name string(255)
  formType string(255)
}

Table SupervisionForm {
  id uuid(36)
  name string(255)
  detail string(255)
  term string(255)
  educationYear string(255)
  supervisionFormTypeid uuid(255) [ref: > SupervisionFormType.id]
  suggestion string(255)
  supervisorName string(255)
}

Table School {
  id uuid
  idSchool string
  name string
  size string
  district string
  email string
  tel string
  address string
  junior string
  senior string
  director string
  nTeacher string
  nPersonnel string
  teachingStyle string
  openClass string
  userId uuid [ref: > User.id]
}

Table SchoolSupervisionForm {
    id uuid
		schoolid uuid [ref: > School.id]
		supervisionFormid uuid
		year string
		term string
}

Table CFSection {
  id uuid(255)
  section string(255)
  haveSubSection string(255)
  priority string(255)
  supervisionFormid uuid(255) [ref: > SupervisionForm.id ]
}

Table CFSubSection {
  	id uuid
		section string
		customFormSectionid uuid
		priority string
}

Table CFQSection {
  	id uuid
		question string
		detail string
		type QuestionTypeEnum
		CFSectionid uuid [ref: > CFSection.id]
		priority string
}


Table CFQSubSection {
    id uuid
		question string
		detail string
		type QuestionTypeEnum
		CFSubSectionid uuid [ref: > CFSubSection.id]
		priority string
}

Table News {
  	id uuid
		name string
		description string
		editor string
		content string
		link string
		img1 string
		img2 string
		img3 string
		img4 string
		img5 string
}

Table Personnel {
    id uuid
		idPersonnel string
		name string
		lastname string
		position string
		group string
		email string
		address string
		tel string
		imgUrl string
		userId uuid [ref: > User.id]
}
Table QF {
		id uuid
		question string
		supervisionFormid uuid [ref: > SupervisionForm.id]
		detail string
		priority string
}

Table ResultCFBQSection {
  	id uuid
		result boolean
		remark string
		file string
		CFQSectionid uuid [ref: > CFQSection.id]
		schoolSupervisionFormid uuid [ref: > SchoolSupervisionForm.id]
}
Table ResultCFBQSubSection {
  	id  string
		result  boolean
		remark  string
		file  string
		CFQSectionId  string [ref: > CFQSection.id]
		schoolSupervisionFormid uuid [ref: > SchoolSupervisionForm.id]
}

Table ResultCFOEQSection {
  	id  string
		result  string
		remark  string
		file  string
		CFQSectionId  string [ref: > CFQSection.id]
		schoolSupervisionFormid uuid [ref: > SchoolSupervisionForm.id]
}

Table ResultCFOEQSubSection {
    id uuid
		result string
		remark string
		file string
		CFQSubSectionid uuid [ref: > CFQSubSection.id]
		schoolSupervisionFormid uuid [ref: > SchoolSupervisionForm.id]
}

Table ResultQFBQ {
  	id uuid
		result boolean
		file any
		QFid uuid [ref: > QF.id]
		schoolSupervisionFormid uuid

}

Table ResultQFOEQ {
    id uuid
		result string
		file any
		QFid uuid [ref: > QF.id]
		schoolSupervisionFormid uuid

}

Table RSFSection {
		id uuid
		section string
		supervisionFormid uuid
		priority string
}

Table RSFQuestion {
  	id uuid
		question string
		RSFSectionid uuid [ref: > RSFSection.id]
		priority string

}

Table ResultRSF {
  	id uuid
		score number
		RSFQuestionid uuid [ref: > RSFQuestion.id]
		schoolid uuid
		schoolSupervisionFormid uuid

}



```
