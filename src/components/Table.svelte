
<script lang="ts">
    import DataTable, { Head, Body, Row, Cell } from '@smui/data-table';
    import Button, { Label, Icon } from '@smui/button';
</script>

<DataTable  style="width: 100%;">
    <Head>
        <Row>
            <Cell >ID</Cell>
            <Cell>Title</Cell>
            <Cell>Image</Cell>
            <Cell>Date Created</Cell>
            <Cell>Actions</Cell>
        </Row>
    </Head>
<Body>
    <Row>
        <Cell>1</Cell>
        <Cell>Red</Cell>
        <Cell>Steve</Cell>
        <Cell>Red</Cell>
        <Cell>
            <Button variant="raised">
                <Label>Edit</Label>
            </Button>
            <Button variant="raised">
                <Label>Delete</Label>
            </Button>
        </Cell>
      </Row>
      <Row>
        <Cell>2</Cell>
        <Cell>Red</Cell>
        <Cell>Sharon</Cell>
        <Cell>Purple</Cell>
        <Cell ><Button variant="raised">
            <Label>Edit</Label>
        </Button>
    
        <Button variant="raised">
            <Label>Delete</Label>
        </Button>

    </Cell>
      </Row>
      <Row>
        <Cell>3</Cell>
        <Cell>Red</Cell>
        <Cell>Rodney</Cell>
        <Cell>Orange</Cell>
        <Cell ><Button variant="raised">
            <Label>Edit</Label>
        </Button>
        <Button variant="raised">
            <Label>Delete</Label>
        </Button>
    </Cell>
      </Row>
      <Row>
        <Cell>4</Cell>
        <Cell>Red</Cell>
        <Cell>Mack</Cell>
        <Cell>Blue</Cell>
        <Cell ><Button variant="raised">
            <Label>Edit</Label>
        </Button>
        <Button variant="raised" class="button-shaped-round">
            <Label>Delete</Label>
        </Button>
    </Cell>
      </Row>
    </Body>

</DataTable>
