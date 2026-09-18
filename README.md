Section 1 — Command Description
What the Tool Does

grepCount is a command that combines grep and wc. It looks in a file for a  word or phrase, shows all the matching lines and shows the total number of matches found.

How to Run It
node grepCount.js <PATTERN> <FILENAME>

Example
node grepCount.js error log.txt

Commands Combined

grepCount is based on the functionality of:

grep (searches for matching text)
wc (counts the number of matches)

Section 2 — AI‑Assisted Programming

What I Asked AI

I asked AI how the grep command works, how files can be read using the fs module, and for advice regarding test cases and edge cases.

Where AI Helped

With the help of AI I was able to understand the grep command, use the fs module to read files, and give me test cases and edge cases for the program.

Where I Had to Think Independently

I needed to work out how grepCount should work, write and test the code, and then make any changes based on the results of the testing.

What AI Got Wrong or Missed

Some AI suggestions had to be tested and modified before they worked in my environment, and I needed to check the output to ensure that the programme worked as I expected .




# grepCount.js



const fs = require('fs');
const path = require('path');

if (process.argv.length !== 4) {
    console.log('Missing Argument');
    console.log(`Usage: node ${path.basename(process.argv[1])} <PATTERN> <FILENAME>`);
    return;
}

let pattern = process.argv[2];
let filename = process.argv[3];

let content = fs.readFileSync(filename, 'utf8');
let lines = content.split('\n');

let matchCount = 0;

for (let line of lines) {
    if (line.includes(pattern)) {
        console.log(line);
        matchCount++;
    }
}

console.log(`\nTotal Matches: ${matchCount}`);
