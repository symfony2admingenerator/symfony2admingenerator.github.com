---
layout: cheat-sheet
title: Admingenerator cheat sheat for *-generator.yml
---

# The generator.yml

## Main configuration

<ul>
	<li>
		<span class="code">generator: admingenerator.generator.<span class="accepted_values">propel|doctrine|doctrine_odm</span></span>
		<span class="doc">The generator service used depending your ORM /ODM</span>
	</li>
	<li>
		<span class="code">params:</span>
		<span class="doc"></span>
		<ul>
			<li>
				<span class="code">model: <span class="example">Your\Model</span> <span class="accepted_values">The model namespace of your class</span></span>
				<span class="doc">Define the model/entity used</span>
			</li>
			<li>
				<span class="code">namespace_prefix: <span class="accepted_values">string</span></span>
				<span class="doc">The base namespace of your generated bundle</span>
			</li>
			<li>
				<span class="code">subfolder: <span class="accepted_values">string</span></span>
				<span class="doc">The subfolders between namespace_prefix and bundle_name in the path of your admin bundle</span>
			</li>
			<li>
				<span class="code">bundle_name: <span class="accepted_values">string</span></span>
				<span class="doc">The bundle name without the namespace_prefix</span>
			</li>
			<li>
				<span class="code">fields: <span class="accepted_values">array</span></span>
				<span class="doc"><a href="#fields-configuration">See fields configuration section</a></span>
			</li>
		</ul>
	</li>
	<li>
		<span class="code">builders:</span>
		<span class="doc"></span>
		<ul>
			<li>
				<span class="code">list: <span class="accepted_values">array</span></span>
				<span class="doc"><a href="#list-configuration">See list configuration section</a></span>
			</li>
			<li>
				<span class="code">filters: <span class="accepted_values">array</span></span>
				<span class="doc"><a href="#filters-configuration">See filters configuration section</a></span>
			</li>
		    <li>
				<span class="code">show: <span class="accepted_values">array</span></span>
				<span class="doc"><a href="#show-configuration">See show configuration section</a></span>
			</li>
			<li>
				<span class="code">new: <span class="accepted_values">array</span></span>
				<span class="doc"><a href="#new-configuration">See new configuration section</a></span>
			</li>
			<li>
				<span class="code">edit: <span class="accepted_values">array</span></span>
				<span class="doc"><a href="#edit-configuration">See edit configuration section</a></span>
			</li>
			<li>
				<span class="code">delete: <span class="accepted_values">array</span></span>
				<span class="doc"><a href="#list-configuration">See delete configuration section</a></span>
			</li>
		</ul>
	</li>
</ul>

## Fields configuration

This section of configuration is valid for all param.fields sections :

<ul>
	<li>
		<span class="code">your_field_name:</span>
		<span class="doc">your_field_name correspond to the field you want to configure</span>
		<ul>
			<li>
				<span class="code">label: <span class="accepted_values">string</span></span>
				<span class="doc">The label of your field</span>
			</li>
			<li>
				<span class="code">getter: <span class="accepted_values">string</span></span>
				<span class="doc">To change the getter used to show the field value</span>
			</li>
			<li>
				<span class="code">help: <span class="accepted_values">string</span></span>
				<span class="doc">Add an help message with your field</span>
			</li>
			<li>
				<span class="code">sort_on: <span class="accepted_values">string</span></span>
				<span class="doc">Change the column to sort the list</span>
			</li>
			<li>
				<span class="code">filter_on: <span class="accepted_values">string</span></span>
				<span class="doc">Change the column used for filtering</span>
			</li>
			<li>
				<span class="code">dbType: <span class="accepted_values">string</span></span>
				<span class="doc">Simulate that your column is another database storage type. (Eg to tell a string is a date, or for virtual columns)</span>
			</li>
			<li>
				<span class="code">formType: <span class="accepted_values">string</span></span>
				<span class="doc">Change the type used in form (eg replace a input text by a choice list)</span>
			</li>
			<li>
				<span class="code">formOptions: <span class="accepted_values">array</span></span>
				<span class="doc">Rewrite all option for your type, key/values of the array is passed to the form field</span>
			</li>
			<li>
				<span class="code">addFormOptions: <span class="accepted_values">array</span></span>
				<span class="doc">Define complentary form option, but keep those ones calculated by the generator</span>
			</li>
			<li>
				<span class="code">credentials: <span class="accepted_values">string</span></span>
				<span class="doc">The credential expression used to secure the field</span>
			</li>
			<li>
				<span class="code">extras: <span class="accepted_values">array</span></span>
				<span class="doc">Extra configurations for specific fields</span>
				<ul>
					<li>
						<span class="code">new_label: <span class="accepted_values">string</span></span>
						<span class="doc">For collection fields, the label used on the add action</span>
					</li>
				</ul>
			</li>
		</ul>
	</li>
</ul>

## List configuration

<ul>
	<li>
		<span class="code">list:</span>
		<span class="doc"></span>
		<ul>
			<li>
				<span class="code">params:</span>
				<span class="doc"></span>
				<ul>
					<li>
						<span class="code">title: List of xxx<span class="accepted_values">string</span></span>
						<span class="doc">The title of the list</span>
					</li>
					<li>
						<span class="code">display: <span class="default_value">~</span> <span class="accepted_values">array</span></span>
						<span class="doc">The list of fields to show in the table (by default <span class="default_value">~</span> admingenrator try to find all fields)</span>
					</li>
					<li>
						<span class="code">sort: <span class="default_value">~</span> <span class="accepted_values">array</span></span>
						<span class="doc">The column to sort and optionally the sorting order (<span class="default_value">ASC</span> by default)</span>
					</li>
					<li>
						<span class="code">fields: <span class="accepted_values">array</span></span>
						<span class="doc"><a href="#fields-configuration">See fields configuration section</a></span>
					</li>
					<li>
						<span class="code">scopes: <span class="accepted_values">array</span></span>
						<span class="doc"><a href="#scopes-configuration">See scopes configuration section</a></span>
					</li>
					<li>
						<span class="code">actions: <span class="accepted_values">array</span></span>
						<span class="doc"><a href="#actions-configuration">See actions configuration section</a></span>
					</li>
					<li>
						<span class="code">batch_actions: <span class="accepted_values">array</span></span>
						<span class="doc"><a href="#batch_actions-configuration">See batch_actions configuration section</a></span>
					</li>
					<li>
						<span class="code">object_actions: <span class="accepted_values">array</span></span>
						<span class="doc"><a href="#object_actions-configuration">See object_actions configuration section</a></span>
					</li>
				</ul>
			</li>
		</ul>
	</li>
</ul>

### Scopes configuration

Scopes enable you to create short filter button on the top of the table

<ul>
	<li>
		<span class="code">scopes:</span></span>
		<span class="doc"></span>
		<ul>
			<li>
				<span class="code">group_name: <span class="accepted_values">array</span></span>
				<span class="doc">Only one scope per group can be activated as same time (group_name is your own group key name)</span>
				<ul>
					<li>
						<span class="code">"Filter name": <span class="accepted_values">array</span></span>
						<span class="doc">The key name correspond of the label for the scope button</span>
						<ul>
							<li>
								<span class="code">default: <span class="default_value">false</span> <span class="accepted_values">boolean</span></span>
								<span class="doc">Is this scope selected by default</span>
							</li>
							<li>
								<span class="code">filters: <span class="accepted_values">array</span></span>
								<span class="doc">Filter to apply when scope is selected</span>
							</li>
						</ul>
					</li>
				</ul>
			</li>
		</ul>
	</li>
</ul>
