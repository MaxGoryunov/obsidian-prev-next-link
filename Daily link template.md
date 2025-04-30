
<%*
const dv = app.plugins.plugins["dataview"].api;
const filename = tp.file.title;
const query = `TABLE WITHOUT ID file.link as "Previous"
FROM "Daily"
WHERE date(file.name, "yyyy-MM-dd") < date("${filename}", "yyyy-MM-dd")
SORT file.name DESC
LIMIT 1`;
const other = `TABLE WITHOUT ID file.link as "Next"
FROM "Daily"
WHERE date(file.name, "yyyy-MM-dd") > date("${filename}", "yyyy-MM-dd")
SORT file.name ASC
LIMIT 1`;

const tFile = tp.file.find_tfile(filename);
const queryOutput = await dv.queryMarkdown(query);
const otherOutput = await dv.queryMarkdown(other);

// write query output to file
// queryOutput.value + otherOutput.value
await app.vault.modify(tFile, queryOutput.value + otherOutput.value);


%>