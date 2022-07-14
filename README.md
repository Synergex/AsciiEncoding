# AsciiEncoding<br />
**Created Date:** 1/27/2009<br />
**Last Updated:** 10/11/2010<br />
**Description:** The ASCIIEncoding class currently has only one method: GetBytes. This method encodes all the characters in the specified String into a sequence of bytes and returns them as a Dynamic System Array of type Byte. It is designed after the .Net Framework's GetBytes method. It can optionally be used in conjunction with the Convert.ToBase64String method (also available on CodeExchange). (Update for Synergy 9.5 compatibility)<br />
**Platforms:** Windows; Unix; OpenVMS<br />
**Products:** Synergy DBL<br />
**Minimum Version:** 9.1.5b<br />
**Author:** Tod Phillips
<hr>

**Additional Information:**
DESCRIPTION: ASCIIEncoding is a class that provides methods to represent an ASCII character
encoding of characters.

ADDITIONAL NOTES: In order to use this class, it must first be prototyped with the DBLPROTO
utility. Ensure that your SYNIMPDIR and SYNEXPDIR environment variables
have been set, then run the protyper by typing:

dblproto ASCIIEncoding

from a command prompt in the directory where the ASCIIEncoding.dbl file has
been saved. (Alternately, import the file into a Workbench project, right-
click the project in the Projects tab and select "Generate Synergy
Protypes..."). The included file can then be compiled and added to any
library or ELB. To use the provided class methods, simply type

import SynPSG.Text.Encoding

at the top of your source code. (See Example, below).

CLASS: ASCIIEncoding (Public)

ENUMERATION(S):
None

CONSTRUCTOR:
None

PROPERTIES:
None

METHOD(S):
GetBytes
Encodes all the characters in the specified String into a sequence of bytes.

Usage & Overloads

ASCIIEncoding.GetBytes(string a_string), [#]@Byte
a_string is a string variable


EXAMPLE(S):

The following program demonstrates the use of the ASCIIEncoding.GetBytes method.

;; Program to demonstrate the ASCIIEncoding.GetBytes method.

import SynPSG.Text.Encoding

main <br />
  record <br />
    byteArray ,[#]@Byte <br />
    oldString ,string <br />
    wrkByte ,@Byte <br />
  endrecord <br />

proc <br />
  open(1,O,'TT:') <br />
  oldString = "This is a test." <br />
  writes(1,"Original String:") <br />
  writes(1,%atrim(oldString)) <br />
  writes(1,"") <br />
  byteArray = ASCIIEncoding.GetBytes(oldString) <br />
  writes(1,"Characters in original string: "+%string(byteArray.Length,'ZZX')) <br />
  writes(1,"Values of each element in the returned byte array:") <br />
  foreach wrkByte in byteArray <br />
    writes(1,%string(wrkByte,'XXX')+" ("+^a(wrkByte)+")") <br />
  end <br />
