listManager
===========

List Manager helps you with adding and removing rows in a list. The list can be made with div's or li's elements.

How to use
----------

To initialise it:

new listManager(el[, options]);

Methods:

.add([options]);

AND

.remove(target);

AND

.removeAll();

Options:

* listElement: The element you want to use for the rows.
* addWhere: From the target, where you want the new row to be. You can use: top, bottom, after and before.
* rowHTML: What HTML you want to see in the row.
* target: The element where the new row will position it self from.
* noTargetAddWhere: If there is no target define in the add method. You can use: top, bottom, after and before.

You can change the options when using the .add([options]) method.

Events:

* onAddedRow: Activated when a new row is added. You get the added row.
* onRemovedRow: Activated when a row is removed. You get the removed row.
* onRemovedAllRows: Activated when a all the rows are removed. You get a array of all the rows you removed.

Tips:

This is a small script to help add buttons to add and remove a row inside a row.

var rowContent = function() {

    var content = new Element('span', {'text': (new Date())});
    
    var removeButton = new Element('a', {
                        'href': '#',
                        'class': 'listmanager-remove-row',
                        'html': '-',
                        'events': {
                            'click': function(el){
                                    list.remove(document.id(el.target).getParent('.listmanager-row'));
                                }
                        }
                    });

    var addButton = new Element('a', {
                        'href': '#',
                        'class': 'listmanager-add-row',
                        'html': '+',
                        'events': {
                            'click': function(el){
                                    list.add({
                                        'rowHTML': rowContent(),
                                        'target': document.id(el.target).getParent('.listmanager-row')
                                    });
                                }
                        }
                    });

    return [addButton, removeButton, content];

};
