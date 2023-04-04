---Title: Simple Persistence---#Simple Persistence- [[randomnote]] [[todo]]- Try this out.- #Simple persistence    - [[SDN]] For data saving, I always start with Ramon’s simple system. Minimal setup and now uses fuel underneath, which is solid and well supported .    - [github repo](https://github.com/seandenigris/Simple-Persistence)    - [discord discussion](https://discord.com/channels/729445214812504107/736333725788274819/1003704307956338789)    - See also the blog post [Simple Image Based Persistence in Squeak](http://onsmalltalk.com/simple-image-based-persistence-in-squeak) by Ramon Leon.- #Address book example    - [[SDN]] If you were going to store a string, you’d probably just use fuel. IMO a framework only starts to make sense at the project level. Here’s an example of a client project: [https://github.com/seandenigris/My-People](https://github.com/seandenigris/My-People)    - Here is the class that handles the persistence for one of the libraries classes, [MpAddressBook](https://github.com/seandenigris/My-People/blob/master/src/MyPeople/MyPeopleDB.class.st)    - And here are the two hooks in that address book class for loading/saving:    - ```language=text
MpAddressBook class >> restoreFrom: anObject 

    default := anObject.
```    - and    - ```language=textMpAddressBook class >> spData

    ^ default
```    - To keep references from breaking, it’s important to save your whole object graph together, so you can specify the DB of other dependent projects to include (the two hooks from above in this case are automatically supplied by the framework). Here’s an example of that:    - ```language=text
DynabookDB class >> #schema

    ^ {
        BabySignLanguageDB.
        BroadcastifyDB.
        ComputerWorldDB.
        FlashcardsStDB.
        IdeasDB.
        LivingLibraryDB.
        SmallWorldDB.
        TheProjectProjectDB.
        UkuleleDB.
        VirtualStashDB.
    }
```