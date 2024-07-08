<%*
// Get the current file's content
let content = tp.file.content;

// Define replacements according to your specifications
const replacements = [
  { from: /\\\(\s/g, to: "$$" }, // Replaces "\( " (with following space)
  { from: /\s\\\)/g, to: "$$" }, // Replaces " \)" (with leading space)
  { from: /\\\(/g, to: "$$" },   // Replaces "\(" (without spaces)
  { from: /\\\)/g, to: "$$" },   // Replaces "\)" (without spaces)
  { from: /\\\[/g, to: "$$$$" },  // Replaces "\[" (without spaces)
  { from: /\\\]/g, to: "$$$$" }   // Replaces "\]" (without spaces)
];

// Perform the replacements
replacements.forEach(replacement => {
  content = content.replace(replacement.from, replacement.to);
});

// Update the file with the new content
await this.app.vault.modify(this.app.workspace.activeLeaf.view.file, content);
%>
