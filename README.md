# Quark Core integration/staging tree
http://www.qrk.cc

Copyright (c) 2009-2014 Bitcoin Core Developers Copyright (c) 2013-2014 Quark Core Developers

What is Quark?
Quark is an experimental new digital currency that enables instant payments to anyone, anywhere in the world. Quark uses peer-to-peer technology to operate with no central authority: managing transactions and issuing money are carried out collectively by the network. Quark Core is the name of open source software which enables the use of this currency.

For more information, as well as an immediately useable, binary version of the Quark Core software, see http://www.qrk.cc/

License
Quark Core is released under the terms of the MIT license. See COPYING for more information or see http://opensource.org/licenses/MIT.

Development process
Developers work in their own trees, then submit pull requests when they think their feature or bug fix is ready.

If it is a simple/trivial/non-controversial change, then one of the Quark development team members simply pulls it.

If it is a more complicated or potentially controversial change, then the patch submitter will be asked to start a discussion (if they haven't already) on the mailing list.

The patch will be accepted if there is broad consensus that it is a good thing. Developers should expect to rework and resubmit patches if the code doesn't match the project's coding conventions (see doc/coding.md) or are controversial.

The master branch is regularly built and tested, but is not guaranteed to be completely stable. Tags are created regularly to indicate new official, stable release versions of Quark.

Testing
Testing and code review is the bottleneck for development; we get more pull requests than we can review and test. Please be patient and help out, and remember this is a security-critical project where any mistake might cost people lots of money.

Automated Testing
Developers are strongly encouraged to write unit tests for new code, and to submit new unit tests for old code. Unit tests can be compiled and run (assuming they weren't disabled in configure) with: make check

Manual Quality Assurance (QA) Testing
Large changes should have a test plan, and should be tested by somebody other than the developer who wrote the code. See https://github.com/bitcoin/QA/ for how to create a test plan.

Development tips and tricks
compiling for debugging

Run configure with the --enable-debug option, then make. Or run configure with CXXFLAGS="-g -ggdb -O0" or whatever debug flags you need.

debug.log

If the code is behaving strangely, take a look in the debug.log file in the data directory; error and debugging message are written there.

The -debug=... command-line option controls debugging; running with just -debug will turn on all categories (and give you a very large debug.log file).

The Qt code routes qDebug() output to debug.log under category "qt": run with -debug=qt to see it.

testnet and regtest modes

Run with the -testnet option to run with "play bitcoins" on the test network, if you are testing multi-machine code that needs to operate across the internet.

If you are testing something that can run on one machine, run with the -regtest option. In regression test mode blocks can be created on-demand; see qa/rpc-tests/ for tests that run in -regest mode.

DEBUG_LOCKORDER

Quark Core is a multithreaded application, and deadlocks or other multithreading bugs can be very difficult to track down. Compiling with -DDEBUG_LOCKORDER (configure CXXFLAGS="-DDEBUG_LOCKORDER -g") inserts run-time checks to keep track of what locks are held, and adds warning to the debug.log file if inconsistencies are detected.
