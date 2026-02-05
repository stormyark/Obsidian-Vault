<%*
// Clean up multiple line breaks in a note
app.vault.process(app.workspace.getActiveFile(), contents => contents.replace(/\n\s*\n/g, '\n\n'))
-%>