contact<-read.csv("W:/GWU2.0/switchpitch/contact.csv")
colnames(contact)

contact$Email<-as.character(contact$Email)
length(contact$Email)
for (i in 1:1864){
  a<-contact$Email[i]
  contact$c[i]<-strsplit(a,'@')[[1]][2]
  contact$c2[i]<-strsplit(contact$c[i],'\\.')[[1]][1]
}

contact$c3<-tolower(contact$c2)

contact$Acc<-tolower(contact$Account.Name)

contact$acc<-gsub(" ","",tolower(contact$Account.Name))

ACC<-contact[,c(5,10)]
ACCu<-unique(ACC)

try <- data.frame(First=character(),
                    Last=character(),
                    Title=character(),
                    email=character(),
                    emailc3=character(),
                    ACCN=character(),
                    
                    stringsAsFactors=FALSE) 
nomatch <- data.frame(First=character(),
                  Last=character(),
                  Title=character(),
                  email=character(),
                  Account=character(),
                  emailc3=character(),
                  stringsAsFactors=FALSE) 

people<-contact[,c(1,2,3,4,8)]
c=c(1:5,8)
for (i in 1:length(people[,1])){
  a<-people$c3[i]
  for (j in 1:length(ACCu[,1])){
    b<-ACCu$acc[j]
    if(grepl(a,b)){
      d<-cbind(people[i,],ACCu[j,1])
      try<-rbind(try,d)
    }
  }
  if (try[nrow(try),5]!=a){
    nomatch<-rbind(nomatch,contact[i,c])
  }
}

write.csv(try,"../try.csv")
write.csv(nomatch,"../nomatch.csv")
