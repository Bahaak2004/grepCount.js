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
