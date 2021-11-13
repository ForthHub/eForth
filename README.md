<h1 align="center">eForth</h1>

## Introduction
This project was done to compare the speeds between c and go regarding a forth Virtual Machine.  Go proved to increase the speed of the virtual machine compared to c by about 10-15%.  Further inline coding increased the speed to 30% but no higher.

ceForth (version 23) by C.H.Ting is ported to golang under this repository.

ceForth is a forth virtual machine coded in c but it's memory `Data[4096]` register, which host the kernel, was compiled using F#.  

As such, it has been very hard to understand the compiled kernel and colon words.  I leave it to the reader to refer to link below for further understanding of the ceForth virtual machine.  

## Quickstart
```sh
# make sure you have go1.12 or higher

# install library
go get -u github.com/fdamador/eForth

# Test eForth library
go run main.go

# Compile eForth library
go build .

# Example1: Run Words Commands shows all available reverse-polish notation commands called Dictionary.
0 0 0 0 ok> words

# Example2: 1 + 3 shows the result on the top of the data stack
0 0 0 0 ok> 1 3 +
1 3 +
0 0 0 4 ok>

# Stack Comments:
#	Stack inputs and outputs are shown in the form: (input1 input2 ... -- output1 output2 ... ) 
# Stack Abbreviations of Data Types
#	n 32 bit integer
#	d 64 bit integer
#	flag Boolean flag, either 0 or -1
#	char ASCII character or a byte
#	addr 32 bit address 

# Example3: creating a new word
# : Name ( input - output ) commands ;
0 0 0 0 ok> : squared ( n - n*n ) dup dup * swap drop ;
: square dup dup * swap drop ;
 0 0 0 0 ok>4 square
4 square
 0 0 0 10 ok>
# By defaul the system is in HEX. To see stack in DECIMAL, then type DECIMAL
0 0 0 10 ok>DECIMAL
DECIMAL
0 0 0 16 ok>

# Exit will copy of modified program memory `Data[4096]`, where * is the data-time stamp.  This can be reused to compile an updated memorey map.
0 0 0 0 ok> bye
bye
 wrote *_rom.txt

# Exit without modified program memory
0 0 0 0 ok> <CLR+c>

```

## Disclaimer
The project is stale and won't have further updates.  It is being uploaded for recording purposes.

There is no guarantee of Stability.

## Reference
[SVFIG ceForth v23](http://forth.org/OffeteStore/2173-ceForth_23.zip)

## License
[GNU](https://github.com/fdamador/eForth/blob/master/LICENSE)
