Ext.ux.grid.FormRowEditing
==========================

Is a modified version of Ext.grid.plugin.RowEditing

Is needs a lot of work but this is a good start

Here is an example...

Ext.create('Ext.grid.Panel',{
	title:'RowEditing Test'
    store   : me.store,
    columns : [
        {
            header   : 'Col 1',
            width    : 100,
            dataIndex: 'immunization_name'
        },
        {
            header   : 'Col 2',
            flex     : 1,
            dataIndex: 'vis_date'

        }
    ],
	/**
	* Here is the Plugin...
	*/
    plugins: Ext.create('Ex.ux.grid.RowFormEditing', {
        autoCancel  : false,
        errorSummary: false,
        clicksToEdit: 1,
        enableRemove: true,
        formItems   : [
            {
                title : 'general',
                xtype : 'container',
                layout: 'vbox',
                items : [
                    {
                        /**
                         * Line one
                         */
                        xtype   : 'fieldcontainer',
                        layout  : 'hbox',
                        defaults: { margin: '0 10 3 0', xtype: 'textfield'},
                        items   : [

                            {
                                xtype          : 'immunizationlivesearch',
                                fieldLabel     : 'Name',
                                hideLabel      : false,
                                itemId         : 'immunization',
                                enableKeyEvents: true,
                                width          : 300,
                                listeners      : {
                                    scope   : me,
                                    'select': me.onOptionType
                                }
                            },

                            {
                                fieldLabel: 'Administrator',
                                name      : 'administered_by',
                                width     : 260

                            },

                            {
                                fieldLabel: 'Info. Statement Given',
                                width     : 295,
                                labelWidth: 180,
                                xtype     : 'datefield',
                                format    : 'Y-m-d H:i:s',
                                name      : 'education_date'
                            }

                        ]

                    },
                    {
                        /**
                         * Line two
                         */
                        xtype   : 'fieldcontainer',
                        layout  : 'hbox',
                        defaults: { margin: '0 10 3 0', xtype: 'textfield' },
                        items   : [

                            {
                                fieldLabel     : 'Code',
                                name           : 'immunization_id',
                                width          : 300,
                                itemId         : 'immuCode',
                                action         : 'immuCode',
                                enableKeyEvents: true

                            },
                            {

                                xtype     : 'numberfield',
                                fieldLabel: 'Dosis Number',
                                name      : 'dosis'
                            },

                            {
                                fieldLabel: 'Date Administered',
                                xtype     : 'datefield',
                                width     : 295,
                                labelWidth: 180,
                                format    : 'Y-m-d',
                                name      : 'administered_date'
                            }

                        ]

                    },
                    {
                        /**
                         * Line three
                         */
                        xtype   : 'fieldcontainer',
                        layout  : 'hbox',
                        defaults: { margin: '0 10 3 0', xtype: 'textfield' },
                        items   : [

                            {
                                fieldLabel: 'Notes',
                                xtype     : 'textfield',
                                width     : 300,
                                name      : 'note'

                            },
                            {
                                fieldLabel: 'Manufacturer',
                                xtype     : 'textfield',
                                width     : 260,

                                name: 'manufacturer'

                            },
                            {
                                fieldLabel: 'Lot Number',
                                xtype     : 'textfield',
                                width     : 295,
                                labelWidth: 180,
                                name      : 'lot_number'

                            }

                        ]

                    }

                ]

            }

        ]
    })
});