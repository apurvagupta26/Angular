1. Debounce Example: Search input handling
You can use a debounce to delay sending search queries until the user stops typing. This helps in reducing the number of unnecessary API calls.

import { Component, OnInit } from '@angular/core';
import { FormControl } from '@angular/forms';
import { debounceTime, distinctUntilChanged } from 'rxjs/operators';

@Component({
  selector: 'app-search',
  template: `
    <input [formControl]="searchControl" placeholder="Search something..." />
  `,
  styleUrls: ['./search.component.css']
})
export class SearchComponent implements OnInit {
  searchControl = new FormControl();

  ngOnInit() {
    // Debounce time to reduce API calls
    this.searchControl.valueChanges.pipe(
      debounceTime(300), // Wait for 300ms pause in typing
      distinctUntilChanged() // Only emit if value is different from last emitted value
    ).subscribe(searchTerm => {
      this.searchItems(searchTerm); // Function to handle the search
    });
  }

  searchItems(query: string) {
    console.log('Searching for:', query);
    // Call your search API here
  }
}

debounceTime(300) will delay the API call by 300ms after the user stops typing.
distinctUntilChanged() ensures that the API is only called if the search term has changed.
